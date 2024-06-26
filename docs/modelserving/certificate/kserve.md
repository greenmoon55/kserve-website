# KServe with Self Signed Certificate Model Registry

If you are using a model registry with a self-signed certificate, you must either skip ssl verify or apply the appropriate CA bundle to the storage-initializer to create a connection with the registry.
This document explains three methods that can be used in KServe, described below:

- Configure CA bundle for storage-initializer
    - Global configuration
    - Namespace scope configuration(Using `storage-config` Secret)
        - json
        - annotation
- Skip SSL Verification
  
(NOTE) This is only available for `RawDeployment` and `ServerlessDeployment`. For modelmesh, you should add ca bundle content into [`certificate` parameter in `storage-config`](https://github.com/kserve/modelmesh-serving/blob/bba0cec8ca8c6c6f19958696f39b27b5b49cadd8/docs/predictors/setup-storage.md?plain=1#L65)
## Configure CA bundle for storage-initializer  
### Global Configuration

KServe use `inferenceservice-config` ConfigMap for default configuration. If you want to add `cabundle` cert for every inference service, you can set `caBundleConfigMapName` in the ConfigMap. Before updating the ConfigMap, you have to create a ConfigMap for CA bundle certificate in the namespace that KServe controller is running and the data key in the ConfigMap must be `cabundle.crt`. 

![Image1](./images/cert-global-way.png)


- Create CA ConfigMap with the CA bundle cert
  ~~~
  kubectl create configmap cabundle --from-file=/path/to/cabundle.crt

  kubectl get configmap cabundle -o yaml
  apiVersion: v1
  data:
    cabundle.crt: XXXXX
  kind: ConfigMap
  metadata:
    name: cabundle
    namespace: kserve
  ~~~
- Update `inferenceservice-config` ConfigMap 
  ~~~
    storageInitializer: |-
    {
        ...
        "caBundleConfigMapName": "cabundle",
        ...
    }
  ~~~
  
After you update this configuration, please restart KServe controller pod to pick up the change.

When you create a inference service, then the ca bundle will be copied to your user namespace and it will be attached to the storage-initializer container.

![Image2](./images/cert-global-ca-bundle.png){ style="display: block; margin: 0 auto" }

### Using storage-config Secret

If you want to apply the cabundle only to a specific inferenceservice, you can use a specific annotation or variable(`cabundle_configmap`) on the `storage-config` Secret used by the inferenceservice.
In this case, you have to create the cabundle ConfigMap in the user namespace before you create the inferenceservice.

![Image3](./images/cert-local-ca-bundle.png){ style="display: block; margin: 0 auto" }


- Create a ConfigMap with the cabundle cert
  ~~~
  kubectl create configmap local-cabundle --from-file=/path/to/cabundle.crt

  kubectl get configmap cabundle -o yaml
  apiVersion: v1
  data:
    cabundle.crt: XXXXX
  kind: ConfigMap
  metadata:
    name: local-cabundle
    namespace: kserve-demo
  ~~~

- Add an annotation `serving.kserve.io/s3-cabundle-configmap` to `storage-config` Secret
  ~~~
  apiVersion: v1
  data:
    AWS_ACCESS_KEY_ID: VEhFQUNDRVNTS0VZ
    AWS_SECRET_ACCESS_KEY: VEhFUEFTU1dPUkQ=
  kind: Secret
  metadata:
    annotations:
      serving.kserve.io/s3-cabundle-configmap: local-cabundle
      ...
    name: storage-config
    namespace: kserve-demo
  type: Opaque
  ~~~

- Or, set a variable `cabundle_configmap` to `storage-config` Secret
  ~~~
  apiVersion: v1
  stringData:
    localMinIO: |
    {
      "type": "s3",
      ....
      "cabundle_configmap": "local-cabundle"
    }
  kind: Secret
  metadata:
    name: storage-config
    namespace: kserve-demo
  type: Opaque
  ~~~

## Skip SSL Verification

For testing purposes or when there is no cabundle, you can easily create an SSL connection by disabling SSL verification.
This can also be used by adding an annotation or setting a variable in `secret-config` Secret.

- Add an annotation(`serving.kserve.io/s3-verifyssl`) to `storage-config` Secret
  ~~~
  apiVersion: v1
  data:
    AWS_ACCESS_KEY_ID: VEhFQUNDRVNTS0VZ
    AWS_SECRET_ACCESS_KEY: VEhFUEFTU1dPUkQ=
  kind: Secret
  metadata:
    annotations:
         serving.kserve.io/s3-verifyssl: "0" # 1 is true, 0 is false
      ...
    name: storage-config
    namespace: kserve-demo
  type: Opaque
  ~~~

- Or, set a variable (`verify_ssl`) to `storage-config` Secret
  ~~~
  apiVersion: v1
  stringData:
    localMinIO: |
      {
        "type": "s3",
        ...
        "verify_ssl": "0"  # 1 is true, 0 is false  (You can set True/true/False/false too)
      }
  kind: Secret
  metadata:
    name: storage-config
    namespace: kserve-demo
  type: Opaque
  ~~~

[Full Demo Scripts](./full-demo.md)
