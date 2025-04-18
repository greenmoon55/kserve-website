<p>Packages:</p>
<ul>
<li>
<a href="#serving.kserve.io/v1alpha1">serving.kserve.io/v1alpha1</a>
</li>
<li>
<a href="#serving.kserve.io/v1beta1">serving.kserve.io/v1beta1</a>
</li>
</ul>
<h2 id="serving.kserve.io/v1alpha1">serving.kserve.io/v1alpha1</h2>
<div>
<p>Package v1alpha1 contains API Schema definitions for the serving v1alpha1 API group</p>
</div>
Resource Types:
<ul></ul>
<h3 id="serving.kserve.io/v1alpha1.BuiltInAdapter">BuiltInAdapter
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>serverType</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServerType">
ServerType
</a>
</em>
</td>
<td>
<p>ServerType must be one of the supported built-in types such as &ldquo;triton&rdquo; or &ldquo;mlserver&rdquo;,
and the runtime&rsquo;s container must have the same name</p>
</td>
</tr>
<tr>
<td>
<code>runtimeManagementPort</code><br/>
<em>
int
</em>
</td>
<td>
<p>Port which the runtime server listens for model management requests</p>
</td>
</tr>
<tr>
<td>
<code>memBufferBytes</code><br/>
<em>
int
</em>
</td>
<td>
<p>Fixed memory overhead to subtract from runtime container&rsquo;s memory allocation to determine model capacity</p>
</td>
</tr>
<tr>
<td>
<code>modelLoadingTimeoutMillis</code><br/>
<em>
int
</em>
</td>
<td>
<p>Timeout for model loading operations in milliseconds</p>
</td>
</tr>
<tr>
<td>
<code>env</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#envvar-v1-core">
[]Kubernetes core/v1.EnvVar
</a>
</em>
</td>
<td>
<p>Environment variables used to control other aspects of the built-in adapter&rsquo;s behaviour (uncommon)</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ClusterLocalModel">ClusterLocalModel
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ClusterLocalModelSpec">
ClusterLocalModelSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>sourceModelUri</code><br/>
<em>
string
</em>
</td>
<td>
<p>Original StorageUri</p>
</td>
</tr>
<tr>
<td>
<code>modelSize</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Model size to make sure it does not exceed the disk space reserved for local models. The limit is defined on the NodeGroup.</p>
</td>
</tr>
<tr>
<td>
<code>nodeGroup</code><br/>
<em>
string
</em>
</td>
<td>
<p>group of nodes to cache the model on.</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ClusterLocalModelStatus">
ClusterLocalModelStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ClusterLocalModelSpec">ClusterLocalModelSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterLocalModel">ClusterLocalModel</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>sourceModelUri</code><br/>
<em>
string
</em>
</td>
<td>
<p>Original StorageUri</p>
</td>
</tr>
<tr>
<td>
<code>modelSize</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Model size to make sure it does not exceed the disk space reserved for local models. The limit is defined on the NodeGroup.</p>
</td>
</tr>
<tr>
<td>
<code>nodeGroup</code><br/>
<em>
string
</em>
</td>
<td>
<p>group of nodes to cache the model on.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ClusterLocalModelStatus">ClusterLocalModelStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterLocalModel">ClusterLocalModel</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>nodeStatus</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.NodeStatus">
map[string]kserve.io/serving/pkg/apis/serving/v1alpha1.NodeStatus
</a>
</em>
</td>
<td>
<p>Status of the model on a node, like NodeDownloaded or NodeNotReady</p>
</td>
</tr>
<tr>
<td>
<code>copies</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ModelCopies">
ModelCopies
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>How many nodes have the model available locally</p>
</td>
</tr>
<tr>
<td>
<code>inferenceServices</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.NamespacedName">
[]NamespacedName
</a>
</em>
</td>
<td>
<p>Inference services using this local model</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ClusterServingRuntime">ClusterServingRuntime
</h3>
<div>
<p>ClusterServingRuntime is the Schema for the servingruntimes API</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">
ServingRuntimeSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>supportedModelFormats</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.SupportedModelFormat">
[]SupportedModelFormat
</a>
</em>
</td>
<td>
<p>Model formats and version supported by this runtime</p>
</td>
</tr>
<tr>
<td>
<code>multiModel</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Whether this ServingRuntime is intended for multi-model usage or not.</p>
</td>
</tr>
<tr>
<td>
<code>disabled</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set to true to disable use of this runtime</p>
</td>
</tr>
<tr>
<td>
<code>protocolVersions</code><br/>
<em>
[]github.com/kserve/kserve/pkg/constants.InferenceServiceProtocol
</em>
</td>
<td>
<em>(Optional)</em>
<p>Supported protocol versions (i.e. v1 or v2 or grpc-v1 or grpc-v2)</p>
</td>
</tr>
<tr>
<td>
<code>workerSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.WorkerSpec">
WorkerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set WorkerSpec to enable multi-node/multi-gpu</p>
</td>
</tr>
<tr>
<td>
<code>ServingRuntimePodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimePodSpec">
ServingRuntimePodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ServingRuntimePodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
<tr>
<td>
<code>grpcEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for internal model-management (implementing mmesh.ModelRuntime gRPC service)
Assumed to be single-model runtime if omitted</p>
</td>
</tr>
<tr>
<td>
<code>grpcDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>httpDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>HTTP endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>replicas</code><br/>
<em>
uint16
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configure the number of replicas in the Deployment generated by this ServingRuntime
If specified, this overrides the podsPerRuntime configuration value</p>
</td>
</tr>
<tr>
<td>
<code>storageHelper</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.StorageHelper">
StorageHelper
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configuration for this runtime&rsquo;s use of the storage helper (model puller)
It is enabled unless explicitly disabled</p>
</td>
</tr>
<tr>
<td>
<code>builtInAdapter</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.BuiltInAdapter">
BuiltInAdapter
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Provide the details about built-in runtime adapter</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimeStatus">
ServingRuntimeStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ClusterStorageContainer">ClusterStorageContainer
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.StorageContainerSpec">
StorageContainerSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>container</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>Container spec for the storage initializer init container</p>
</td>
</tr>
<tr>
<td>
<code>supportedUriFormats</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.SupportedUriFormat">
[]SupportedUriFormat
</a>
</em>
</td>
<td>
<p>List of URI formats that this container supports</p>
</td>
</tr>
<tr>
<td>
<code>workloadType</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.WorkloadType">
WorkloadType
</a>
</em>
</td>
<td>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>disabled</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceGraph">InferenceGraph
</h3>
<div>
<p>InferenceGraph is the Schema for the InferenceGraph API for multiple models</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceGraphSpec">
InferenceGraphSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>nodes</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceRouter">
map[string]kserve.io/serving/pkg/apis/serving/v1alpha1.InferenceRouter
</a>
</em>
</td>
<td>
<p>Map of InferenceGraph router nodes
Each node defines the router which can be different routing types</p>
</td>
</tr>
<tr>
<td>
<code>resources</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#resourcerequirements-v1-core">
Kubernetes core/v1.ResourceRequirements
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>affinity</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#affinity-v1-core">
Kubernetes core/v1.Affinity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>timeout</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>TimeoutSeconds specifies the number of seconds to wait before timing out a request to the component.</p>
</td>
</tr>
<tr>
<td>
<code>minReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Minimum number of replicas, defaults to 1 but can be set to 0 to enable scale-to-zero.</p>
</td>
</tr>
<tr>
<td>
<code>maxReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Maximum number of replicas for autoscaling.</p>
</td>
</tr>
<tr>
<td>
<code>scaleTarget</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleTarget specifies the integer target value of the metric type the Autoscaler watches for.
concurrency and rps targets are supported by Knative Pod Autoscaler
(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-targets/">https://knative.dev/docs/serving/autoscaling/autoscaling-targets/</a>).</p>
</td>
</tr>
<tr>
<td>
<code>scaleMetric</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ScaleMetric">
ScaleMetric
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleMetric defines the scaling metric type watched by autoscaler
possible values are concurrency, rps, cpu, memory. concurrency, rps are supported via
Knative Pod Autoscaler(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-metrics">https://knative.dev/docs/serving/autoscaling/autoscaling-metrics</a>).</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceGraphStatus">
InferenceGraphStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceGraphSpec">InferenceGraphSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceGraph">InferenceGraph</a>)
</p>
<div>
<p>InferenceGraphSpec defines the InferenceGraph spec</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>nodes</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceRouter">
map[string]kserve.io/serving/pkg/apis/serving/v1alpha1.InferenceRouter
</a>
</em>
</td>
<td>
<p>Map of InferenceGraph router nodes
Each node defines the router which can be different routing types</p>
</td>
</tr>
<tr>
<td>
<code>resources</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#resourcerequirements-v1-core">
Kubernetes core/v1.ResourceRequirements
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>affinity</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#affinity-v1-core">
Kubernetes core/v1.Affinity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
<tr>
<td>
<code>timeout</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>TimeoutSeconds specifies the number of seconds to wait before timing out a request to the component.</p>
</td>
</tr>
<tr>
<td>
<code>minReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Minimum number of replicas, defaults to 1 but can be set to 0 to enable scale-to-zero.</p>
</td>
</tr>
<tr>
<td>
<code>maxReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Maximum number of replicas for autoscaling.</p>
</td>
</tr>
<tr>
<td>
<code>scaleTarget</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleTarget specifies the integer target value of the metric type the Autoscaler watches for.
concurrency and rps targets are supported by Knative Pod Autoscaler
(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-targets/">https://knative.dev/docs/serving/autoscaling/autoscaling-targets/</a>).</p>
</td>
</tr>
<tr>
<td>
<code>scaleMetric</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ScaleMetric">
ScaleMetric
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleMetric defines the scaling metric type watched by autoscaler
possible values are concurrency, rps, cpu, memory. concurrency, rps are supported via
Knative Pod Autoscaler(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-metrics">https://knative.dev/docs/serving/autoscaling/autoscaling-metrics</a>).</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceGraphStatus">InferenceGraphStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceGraph">InferenceGraph</a>)
</p>
<div>
<p>InferenceGraphStatus defines the InferenceGraph conditions and status</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>Status</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Status">
knative.dev/pkg/apis/duck/v1.Status
</a>
</em>
</td>
<td>
<p>
(Members of <code>Status</code> are embedded into this type.)
</p>
<p>Conditions for InferenceGraph</p>
</td>
</tr>
<tr>
<td>
<code>url</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Url for the InferenceGraph</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceGraphValidator">InferenceGraphValidator
</h3>
<div>
<p>InferenceGraphValidator is responsible for setting default values on the InferenceGraph resources
when created or updated.</p>
<p>NOTE: The +kubebuilder:object:generate=false and +k8s:deepcopy-gen=false marker prevents controller-gen from generating DeepCopy methods,
as it is used only for temporary operations and does not need to be deeply copied.</p>
</div>
<h3 id="serving.kserve.io/v1alpha1.InferenceRouter">InferenceRouter
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceGraphSpec">InferenceGraphSpec</a>)
</p>
<div>
<p>InferenceRouter defines the router for each InferenceGraph node with one or multiple steps</p>
<pre><code class="language-yaml">kind: InferenceGraph
metadata:
name: canary-route
spec:
nodes:
root:
routerType: Splitter
routes:
- service: mymodel1
weight: 20
- service: mymodel2
weight: 80
</code></pre>
<pre><code class="language-yaml">kind: InferenceGraph
metadata:
name: abtest
spec:
nodes:
mymodel:
routerType: Switch
routes:
- service: mymodel1
condition: &quot;{ .input.userId == 1 }&quot;
- service: mymodel2
condition: &quot;{ .input.userId == 2 }&quot;
</code></pre>
<p>Scoring a case using a model ensemble consists of scoring it using each model separately,
then combining the results into a single scoring result using one of the pre-defined combination methods.</p>
<p>Tree Ensemble constitutes a case where simple algorithms for combining results of either classification or regression trees are well known.
Multiple classification trees, for example, are commonly combined using a &ldquo;majority-vote&rdquo; method.
Multiple regression trees are often combined using various averaging techniques.
e.g tagging models with segment identifiers and weights to be used for their combination in these ways.</p>
<pre><code class="language-yaml">kind: InferenceGraph
metadata:
name: ensemble
spec:
nodes:
root:
routerType: Sequence
routes:
- service: feast
- nodeName: ensembleModel
data: $response
ensembleModel:
routerType: Ensemble
routes:
- service: sklearn-model
- service: xgboost-model
</code></pre>
<p>Scoring a case using a sequence, or chain of models allows the output of one model to be passed in as input to the subsequent models.</p>
<pre><code class="language-yaml">kind: InferenceGraph
metadata:
name: model-chainer
spec:
nodes:
root:
routerType: Sequence
routes:
- service: mymodel-s1
- service: mymodel-s2
data: $response
- service: mymodel-s3
data: $response
</code></pre>
<p>In the flow described below, the pre_processing node base64 encodes the image and passes it to two model nodes in the flow.
The encoded data is available to both these nodes for classification. The second node i.e. dog-breed-classification takes the
original input from the pre_processing node along-with the response from the cat-dog-classification node to do further classification
of the dog breed if required.</p>
<pre><code class="language-yaml">kind: InferenceGraph
metadata:
name: dog-breed-classification
spec:
nodes:
root:
routerType: Sequence
routes:
- service: cat-dog-classifier
- nodeName: breed-classifier
data: $request
breed-classifier:
routerType: Switch
routes:
- service: dog-breed-classifier
condition: { .predictions.class == &quot;dog&quot; }
- service: cat-breed-classifier
condition: { .predictions.class == &quot;cat&quot; }
</code></pre>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>routerType</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceRouterType">
InferenceRouterType
</a>
</em>
</td>
<td>
<p>RouterType</p>
<ul>
<li><p><code>Sequence:</code> chain multiple inference steps with input/output from previous step</p></li>
<li><p><code>Splitter:</code> randomly routes to the target service according to the weight</p></li>
<li><p><code>Ensemble:</code> routes the request to multiple models and then merge the responses</p></li>
<li><p><code>Switch:</code> routes the request to one of the steps based on condition</p></li>
</ul>
</td>
</tr>
<tr>
<td>
<code>steps</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceStep">
[]InferenceStep
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Steps defines destinations for the current router node</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceRouterType">InferenceRouterType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceRouter">InferenceRouter</a>)
</p>
<div>
<p>InferenceRouterType constant for inference routing types</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Ensemble&#34;</p></td>
<td><p>Ensemble router routes the requests to multiple models and then merge the responses</p>
</td>
</tr><tr><td><p>&#34;Sequence&#34;</p></td>
<td><p>Sequence Default type only route to one destination</p>
</td>
</tr><tr><td><p>&#34;Splitter&#34;</p></td>
<td><p>Splitter router randomly routes the requests to the named service according to the weight</p>
</td>
</tr><tr><td><p>&#34;Switch&#34;</p></td>
<td><p>Switch routes the request to the model based on certain condition</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceStep">InferenceStep
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceRouter">InferenceRouter</a>)
</p>
<div>
<p>InferenceStep defines the inference target of the current step with condition, weights and data.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Unique name for the step within this node</p>
</td>
</tr>
<tr>
<td>
<code>InferenceTarget</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceTarget">
InferenceTarget
</a>
</em>
</td>
<td>
<p>
(Members of <code>InferenceTarget</code> are embedded into this type.)
</p>
<p>Node or service used to process this step</p>
</td>
</tr>
<tr>
<td>
<code>data</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>request data sent to the next route with input/output from the previous step
$request
$response.predictions</p>
</td>
</tr>
<tr>
<td>
<code>weight</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>the weight for split of the traffic, only used for Split Router
when weight is specified all the routing targets should be sum to 100</p>
</td>
</tr>
<tr>
<td>
<code>condition</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>routing based on the condition</p>
</td>
</tr>
<tr>
<td>
<code>dependency</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.InferenceStepDependencyType">
InferenceStepDependencyType
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>to decide whether a step is a hard or a soft dependency in the Inference Graph</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceStepDependencyType">InferenceStepDependencyType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceStep">InferenceStep</a>)
</p>
<div>
<p>InferenceStepDependencyType constant for inference step dependency</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;Hard&#34;</p></td>
<td><p>Hard</p>
</td>
</tr><tr><td><p>&#34;Soft&#34;</p></td>
<td><p>Soft</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.InferenceTarget">InferenceTarget
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceStep">InferenceStep</a>)
</p>
<div>
<p>Exactly one InferenceTarget field must be specified</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>nodeName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The node name for routing as next step</p>
</td>
</tr>
<tr>
<td>
<code>serviceName</code><br/>
<em>
string
</em>
</td>
<td>
<p>named reference for InferenceService</p>
</td>
</tr>
<tr>
<td>
<code>serviceUrl</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>InferenceService URL, mutually exclusive with ServiceName</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.LocalModelNodeGroup">LocalModelNodeGroup
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.LocalModelNodeGroupSpec">
LocalModelNodeGroupSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>storageLimit</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Max storage size per node in this node group</p>
</td>
</tr>
<tr>
<td>
<code>persistentVolumeSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#persistentvolumespec-v1-core">
Kubernetes core/v1.PersistentVolumeSpec
</a>
</em>
</td>
<td>
<p>Used to create PersistentVolumes for downloading models and in inference service namespaces</p>
</td>
</tr>
<tr>
<td>
<code>persistentVolumeClaimSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#persistentvolumeclaimspec-v1-core">
Kubernetes core/v1.PersistentVolumeClaimSpec
</a>
</em>
</td>
<td>
<p>Used to create PersistentVolumeClaims for download and in inference service namespaces</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.LocalModelNodeGroupStatus">
LocalModelNodeGroupStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.LocalModelNodeGroupSpec">LocalModelNodeGroupSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.LocalModelNodeGroup">LocalModelNodeGroup</a>)
</p>
<div>
<p>LocalModelNodeGroupSpec defines a group of nodes for to download the model to.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>storageLimit</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Max storage size per node in this node group</p>
</td>
</tr>
<tr>
<td>
<code>persistentVolumeSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#persistentvolumespec-v1-core">
Kubernetes core/v1.PersistentVolumeSpec
</a>
</em>
</td>
<td>
<p>Used to create PersistentVolumes for downloading models and in inference service namespaces</p>
</td>
</tr>
<tr>
<td>
<code>persistentVolumeClaimSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#persistentvolumeclaimspec-v1-core">
Kubernetes core/v1.PersistentVolumeClaimSpec
</a>
</em>
</td>
<td>
<p>Used to create PersistentVolumeClaims for download and in inference service namespaces</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.LocalModelNodeGroupStatus">LocalModelNodeGroupStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.LocalModelNodeGroup">LocalModelNodeGroup</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>used</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Used storage space on any node for this node group</p>
</td>
</tr>
<tr>
<td>
<code>available</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Available storage space on any node for this node group</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ModelCopies">ModelCopies
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterLocalModelStatus">ClusterLocalModelStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>available</code><br/>
<em>
int
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>total</code><br/>
<em>
int
</em>
</td>
<td>
<p>Total number of nodes that we expect the model to be downloaded. Including nodes that are not ready</p>
</td>
</tr>
<tr>
<td>
<code>failed</code><br/>
<em>
int
</em>
</td>
<td>
<p>Download Failed</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ModelSpec">ModelSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.TrainedModelSpec">TrainedModelSpec</a>)
</p>
<div>
<p>ModelSpec describes a TrainedModel</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>storageUri</code><br/>
<em>
string
</em>
</td>
<td>
<p>Storage URI for the model repository</p>
</td>
</tr>
<tr>
<td>
<code>framework</code><br/>
<em>
string
</em>
</td>
<td>
<p>Machine Learning <framework name>
The values could be: &ldquo;tensorflow&rdquo;,&ldquo;pytorch&rdquo;,&ldquo;sklearn&rdquo;,&ldquo;onnx&rdquo;,&ldquo;xgboost&rdquo;, &ldquo;myawesomeinternalframework&rdquo; etc.</p>
</td>
</tr>
<tr>
<td>
<code>memory</code><br/>
<em>
k8s.io/apimachinery/pkg/api/resource.Quantity
</em>
</td>
<td>
<p>Maximum memory this model will consume, this field is used to decide if a model server has enough memory to load this model.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.NamespacedName">NamespacedName
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterLocalModelStatus">ClusterLocalModelStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>namespace</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>name</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.NodeStatus">NodeStatus
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterLocalModelStatus">ClusterLocalModelStatus</a>)
</p>
<div>
<p>NodeStatus enum</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;NodeDeleted&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDeleting&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDeletionError&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDownloadError&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDownloadPending&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDownloaded&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeDownloading&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;NodeNotReady&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ScaleMetric">ScaleMetric
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.InferenceGraphSpec">InferenceGraphSpec</a>)
</p>
<div>
<p>ScaleMetric enum</p>
</div>
<h3 id="serving.kserve.io/v1alpha1.ServerType">ServerType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.BuiltInAdapter">BuiltInAdapter</a>)
</p>
<div>
<p>ServerType constant for specifying the runtime name</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;mlserver&#34;</p></td>
<td><p>Model server is MLServer</p>
</td>
</tr><tr><td><p>&#34;ovms&#34;</p></td>
<td><p>Model server is OpenVino Model Server</p>
</td>
</tr><tr><td><p>&#34;triton&#34;</p></td>
<td><p>Model server is Triton</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ServingRuntime">ServingRuntime
</h3>
<div>
<p>ServingRuntime is the Schema for the servingruntimes API</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">
ServingRuntimeSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>supportedModelFormats</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.SupportedModelFormat">
[]SupportedModelFormat
</a>
</em>
</td>
<td>
<p>Model formats and version supported by this runtime</p>
</td>
</tr>
<tr>
<td>
<code>multiModel</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Whether this ServingRuntime is intended for multi-model usage or not.</p>
</td>
</tr>
<tr>
<td>
<code>disabled</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set to true to disable use of this runtime</p>
</td>
</tr>
<tr>
<td>
<code>protocolVersions</code><br/>
<em>
[]github.com/kserve/kserve/pkg/constants.InferenceServiceProtocol
</em>
</td>
<td>
<em>(Optional)</em>
<p>Supported protocol versions (i.e. v1 or v2 or grpc-v1 or grpc-v2)</p>
</td>
</tr>
<tr>
<td>
<code>workerSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.WorkerSpec">
WorkerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set WorkerSpec to enable multi-node/multi-gpu</p>
</td>
</tr>
<tr>
<td>
<code>ServingRuntimePodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimePodSpec">
ServingRuntimePodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ServingRuntimePodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
<tr>
<td>
<code>grpcEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for internal model-management (implementing mmesh.ModelRuntime gRPC service)
Assumed to be single-model runtime if omitted</p>
</td>
</tr>
<tr>
<td>
<code>grpcDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>httpDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>HTTP endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>replicas</code><br/>
<em>
uint16
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configure the number of replicas in the Deployment generated by this ServingRuntime
If specified, this overrides the podsPerRuntime configuration value</p>
</td>
</tr>
<tr>
<td>
<code>storageHelper</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.StorageHelper">
StorageHelper
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configuration for this runtime&rsquo;s use of the storage helper (model puller)
It is enabled unless explicitly disabled</p>
</td>
</tr>
<tr>
<td>
<code>builtInAdapter</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.BuiltInAdapter">
BuiltInAdapter
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Provide the details about built-in runtime adapter</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimeStatus">
ServingRuntimeStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ServingRuntimePodSpec">ServingRuntimePodSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec</a>, <a href="#serving.kserve.io/v1alpha1.WorkerSpec">WorkerSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>containers</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
[]Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>List of containers belonging to the pod.
Containers cannot currently be added or removed.
There must be at least one container in a Pod.
Cannot be updated.</p>
</td>
</tr>
<tr>
<td>
<code>volumes</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#volume-v1-core">
[]Kubernetes core/v1.Volume
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>List of volumes that can be mounted by containers belonging to the pod.
More info: <a href="https://kubernetes.io/docs/concepts/storage/volumes">https://kubernetes.io/docs/concepts/storage/volumes</a></p>
</td>
</tr>
<tr>
<td>
<code>nodeSelector</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>NodeSelector is a selector which must be true for the pod to fit on a node.
Selector which must match a node&rsquo;s labels for the pod to be scheduled on that node.
More info: <a href="https://kubernetes.io/docs/concepts/configuration/assign-pod-node/">https://kubernetes.io/docs/concepts/configuration/assign-pod-node/</a></p>
</td>
</tr>
<tr>
<td>
<code>affinity</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#affinity-v1-core">
Kubernetes core/v1.Affinity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the pod&rsquo;s scheduling constraints</p>
</td>
</tr>
<tr>
<td>
<code>tolerations</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#toleration-v1-core">
[]Kubernetes core/v1.Toleration
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the pod&rsquo;s tolerations.</p>
</td>
</tr>
<tr>
<td>
<code>labels</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Labels that will be add to the pod.
More info: <a href="http://kubernetes.io/docs/user-guide/labels">http://kubernetes.io/docs/user-guide/labels</a></p>
</td>
</tr>
<tr>
<td>
<code>annotations</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Annotations that will be add to the pod.
More info: <a href="http://kubernetes.io/docs/user-guide/annotations">http://kubernetes.io/docs/user-guide/annotations</a></p>
</td>
</tr>
<tr>
<td>
<code>imagePullSecrets</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#localobjectreference-v1-core">
[]Kubernetes core/v1.LocalObjectReference
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ImagePullSecrets is an optional list of references to secrets in the same namespace to use for pulling any of the images used by this PodSpec.
If specified, these secrets will be passed to individual puller implementations for them to use. For example,
in the case of docker, only DockerConfig type secrets are honored.
More info: <a href="https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod">https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod</a></p>
</td>
</tr>
<tr>
<td>
<code>hostIPC</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Use the host&rsquo;s ipc namespace.
Optional: Default to false.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterServingRuntime">ClusterServingRuntime</a>, <a href="#serving.kserve.io/v1alpha1.ServingRuntime">ServingRuntime</a>, <a href="#serving.kserve.io/v1alpha1.SupportedRuntime">SupportedRuntime</a>)
</p>
<div>
<p>ServingRuntimeSpec defines the desired state of ServingRuntime. This spec is currently provisional
and are subject to change as details regarding single-model serving and multi-model serving
are hammered out.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>supportedModelFormats</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.SupportedModelFormat">
[]SupportedModelFormat
</a>
</em>
</td>
<td>
<p>Model formats and version supported by this runtime</p>
</td>
</tr>
<tr>
<td>
<code>multiModel</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Whether this ServingRuntime is intended for multi-model usage or not.</p>
</td>
</tr>
<tr>
<td>
<code>disabled</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set to true to disable use of this runtime</p>
</td>
</tr>
<tr>
<td>
<code>protocolVersions</code><br/>
<em>
[]github.com/kserve/kserve/pkg/constants.InferenceServiceProtocol
</em>
</td>
<td>
<em>(Optional)</em>
<p>Supported protocol versions (i.e. v1 or v2 or grpc-v1 or grpc-v2)</p>
</td>
</tr>
<tr>
<td>
<code>workerSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.WorkerSpec">
WorkerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set WorkerSpec to enable multi-node/multi-gpu</p>
</td>
</tr>
<tr>
<td>
<code>ServingRuntimePodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimePodSpec">
ServingRuntimePodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ServingRuntimePodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
<tr>
<td>
<code>grpcEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for internal model-management (implementing mmesh.ModelRuntime gRPC service)
Assumed to be single-model runtime if omitted</p>
</td>
</tr>
<tr>
<td>
<code>grpcDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Grpc endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>httpDataEndpoint</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>HTTP endpoint for inferencing</p>
</td>
</tr>
<tr>
<td>
<code>replicas</code><br/>
<em>
uint16
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configure the number of replicas in the Deployment generated by this ServingRuntime
If specified, this overrides the podsPerRuntime configuration value</p>
</td>
</tr>
<tr>
<td>
<code>storageHelper</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.StorageHelper">
StorageHelper
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configuration for this runtime&rsquo;s use of the storage helper (model puller)
It is enabled unless explicitly disabled</p>
</td>
</tr>
<tr>
<td>
<code>builtInAdapter</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.BuiltInAdapter">
BuiltInAdapter
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Provide the details about built-in runtime adapter</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.ServingRuntimeStatus">ServingRuntimeStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterServingRuntime">ClusterServingRuntime</a>, <a href="#serving.kserve.io/v1alpha1.ServingRuntime">ServingRuntime</a>)
</p>
<div>
<p>ServingRuntimeStatus defines the observed state of ServingRuntime</p>
</div>
<h3 id="serving.kserve.io/v1alpha1.StorageContainerSpec">StorageContainerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ClusterStorageContainer">ClusterStorageContainer</a>)
</p>
<div>
<p>StorageContainerSpec defines the container spec for the storage initializer init container, and the protocols it supports.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>container</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>Container spec for the storage initializer init container</p>
</td>
</tr>
<tr>
<td>
<code>supportedUriFormats</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.SupportedUriFormat">
[]SupportedUriFormat
</a>
</em>
</td>
<td>
<p>List of URI formats that this container supports</p>
</td>
</tr>
<tr>
<td>
<code>workloadType</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.WorkloadType">
WorkloadType
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.StorageHelper">StorageHelper
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>disabled</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.SupportedModelFormat">SupportedModelFormat
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code><br/>
<em>
string
</em>
</td>
<td>
<p>Name of the model format.</p>
</td>
</tr>
<tr>
<td>
<code>version</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Version of the model format.
Used in validating that a predictor is supported by a runtime.
Can be &ldquo;major&rdquo;, &ldquo;major.minor&rdquo; or &ldquo;major.minor.patch&rdquo;.</p>
</td>
</tr>
<tr>
<td>
<code>autoSelect</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set to true to allow the ServingRuntime to be used for automatic model placement if
this model format is specified with no explicit runtime.</p>
</td>
</tr>
<tr>
<td>
<code>priority</code><br/>
<em>
int32
</em>
</td>
<td>
<em>(Optional)</em>
<p>Priority of this serving runtime for auto selection.
This is used to select the serving runtime if more than one serving runtime supports the same model format.
The value should be greater than zero.  The higher the value, the higher the priority.
Priority is not considered if AutoSelect is either false or not specified.
Priority can be overridden by specifying the runtime in the InferenceService.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.SupportedRuntime">SupportedRuntime
</h3>
<div>
<p>SupportedRuntime is the schema for supported runtime result of automatic selection</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>Name</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>Spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">
ServingRuntimeSpec
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.SupportedUriFormat">SupportedUriFormat
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.StorageContainerSpec">StorageContainerSpec</a>)
</p>
<div>
<p>SupportedUriFormat can be either prefix or regex. Todo: Add validation that only one of them is set.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>prefix</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>regex</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.TrainedModel">TrainedModel
</h3>
<div>
<p>TrainedModel is the Schema for the TrainedModel API</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.TrainedModelSpec">
TrainedModelSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>inferenceService</code><br/>
<em>
string
</em>
</td>
<td>
<p>parent inference service to deploy to</p>
</td>
</tr>
<tr>
<td>
<code>model</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ModelSpec">
ModelSpec
</a>
</em>
</td>
<td>
<p>Predictor model spec</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.TrainedModelStatus">
TrainedModelStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.TrainedModelSpec">TrainedModelSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.TrainedModel">TrainedModel</a>)
</p>
<div>
<p>TrainedModelSpec defines the TrainedModel spec</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>inferenceService</code><br/>
<em>
string
</em>
</td>
<td>
<p>parent inference service to deploy to</p>
</td>
</tr>
<tr>
<td>
<code>model</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ModelSpec">
ModelSpec
</a>
</em>
</td>
<td>
<p>Predictor model spec</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.TrainedModelStatus">TrainedModelStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.TrainedModel">TrainedModel</a>)
</p>
<div>
<p>TrainedModelStatus defines the observed state of TrainedModel</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>Status</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Status">
knative.dev/pkg/apis/duck/v1.Status
</a>
</em>
</td>
<td>
<p>
(Members of <code>Status</code> are embedded into this type.)
</p>
<p>Conditions for trained model</p>
</td>
</tr>
<tr>
<td>
<code>url</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<p>URL holds the url that will distribute traffic over the provided traffic targets.
For v1: http[s]://{route-name}.{route-namespace}.{cluster-level-suffix}/v1/models/<trainedmodel>:predict
For v2: http[s]://{route-name}.{route-namespace}.{cluster-level-suffix}/v2/models/<trainedmodel>/infer</p>
</td>
</tr>
<tr>
<td>
<code>address</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Addressable">
knative.dev/pkg/apis/duck/v1.Addressable
</a>
</em>
</td>
<td>
<p>Addressable endpoint for the deployed trained model
http://<inferenceservice.metadata.name>/v1/models/<trainedmodel>.metadata.name</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.TrainedModelValidator">TrainedModelValidator
</h3>
<div>
<p>TrainedModelValidator is responsible for setting default values on the TrainedModel resources
when created or updated.</p>
<p>NOTE: The +kubebuilder:object:generate=false and +k8s:deepcopy-gen=false marker prevents controller-gen from generating DeepCopy methods,
as it is used only for temporary operations and does not need to be deeply copied.</p>
</div>
<h3 id="serving.kserve.io/v1alpha1.WorkerSpec">WorkerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.ServingRuntimeSpec">ServingRuntimeSpec</a>)
</p>
<div>
<p>WorkerSpec is the schema for multi-node/multi-GPU feature</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>ServingRuntimePodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1alpha1.ServingRuntimePodSpec">
ServingRuntimePodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ServingRuntimePodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
<tr>
<td>
<code>size</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configure the number of replicas in the worker set, each worker set represents the unit of scaling</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1alpha1.WorkloadType">WorkloadType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1alpha1.StorageContainerSpec">StorageContainerSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;initContainer&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;localModelDownloadJob&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<hr/>
<p><em>
Generated with <code>gen-crd-api-reference-docs</code>
on git commit <code>7e436424</code>.
</em></p>
<h2 id="serving.kserve.io/v1beta1">serving.kserve.io/v1beta1</h2>
<div>
<p>Package v1beta1 contains API Schema definitions for the serving v1beta1 API group</p>
</div>
Resource Types:
<ul></ul>
<h3 id="serving.kserve.io/v1beta1.ARTExplainerSpec">ARTExplainerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ExplainerSpec">ExplainerSpec</a>)
</p>
<div>
<p>ARTExplainerType defines the arguments for configuring an ART Explanation Server</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>type</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ARTExplainerType">
ARTExplainerType
</a>
</em>
</td>
<td>
<p>The type of ART explainer</p>
</td>
</tr>
<tr>
<td>
<code>ExplainerExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ExplainerExtensionSpec">
ExplainerExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ExplainerExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all explainers</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ARTExplainerType">ARTExplainerType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ARTExplainerSpec">ARTExplainerSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;SquareAttack&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.Batcher">Batcher
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">ComponentExtensionSpec</a>)
</p>
<div>
<p>Batcher specifies optional payload batching available for all components</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>maxBatchSize</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the max number of requests to trigger a batch</p>
</td>
</tr>
<tr>
<td>
<code>maxLatency</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the max latency to trigger a batch</p>
</td>
</tr>
<tr>
<td>
<code>timeout</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the timeout of a batch</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.Component">Component
</h3>
<div>
<p>Component interface is implemented by all specs that contain component implementations, e.g. PredictorSpec, ExplainerSpec, TransformerSpec.</p>
</div>
<h3 id="serving.kserve.io/v1beta1.ComponentExtensionSpec">ComponentExtensionSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ExplainerSpec">ExplainerSpec</a>, <a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>, <a href="#serving.kserve.io/v1beta1.TransformerSpec">TransformerSpec</a>)
</p>
<div>
<p>ComponentExtensionSpec defines the deployment configuration for a given InferenceService component</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>minReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Minimum number of replicas, defaults to 1 but can be set to 0 to enable scale-to-zero.</p>
</td>
</tr>
<tr>
<td>
<code>maxReplicas</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Maximum number of replicas for autoscaling.</p>
</td>
</tr>
<tr>
<td>
<code>scaleTarget</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleTarget specifies the integer target value of the metric type the Autoscaler watches for.
concurrency and rps targets are supported by Knative Pod Autoscaler
(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-targets/">https://knative.dev/docs/serving/autoscaling/autoscaling-targets/</a>).</p>
</td>
</tr>
<tr>
<td>
<code>scaleMetric</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ScaleMetric">
ScaleMetric
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ScaleMetric defines the scaling metric type watched by autoscaler
possible values are concurrency, rps, cpu, memory. concurrency, rps are supported via
Knative Pod Autoscaler(<a href="https://knative.dev/docs/serving/autoscaling/autoscaling-metrics">https://knative.dev/docs/serving/autoscaling/autoscaling-metrics</a>).</p>
</td>
</tr>
<tr>
<td>
<code>containerConcurrency</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>ContainerConcurrency specifies how many requests can be processed concurrently, this sets the hard limit of the container
concurrency(<a href="https://knative.dev/docs/serving/autoscaling/concurrency">https://knative.dev/docs/serving/autoscaling/concurrency</a>).</p>
</td>
</tr>
<tr>
<td>
<code>timeout</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>TimeoutSeconds specifies the number of seconds to wait before timing out a request to the component.</p>
</td>
</tr>
<tr>
<td>
<code>canaryTrafficPercent</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>CanaryTrafficPercent defines the traffic split percentage between the candidate revision and the last ready revision</p>
</td>
</tr>
<tr>
<td>
<code>logger</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.LoggerSpec">
LoggerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Activate request/response logging and logger configurations</p>
</td>
</tr>
<tr>
<td>
<code>batcher</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.Batcher">
Batcher
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Activate request batching and batching configurations</p>
</td>
</tr>
<tr>
<td>
<code>labels</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Labels that will be added to the component pod.
More info: <a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/">https://kubernetes.io/docs/concepts/overview/working-with-objects/labels/</a></p>
</td>
</tr>
<tr>
<td>
<code>annotations</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Annotations that will be added to the component pod.
More info: <a href="https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/">https://kubernetes.io/docs/concepts/overview/working-with-objects/annotations/</a></p>
</td>
</tr>
<tr>
<td>
<code>deploymentStrategy</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#deploymentstrategy-v1-apps">
Kubernetes apps/v1.DeploymentStrategy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>The deployment strategy to use to replace existing pods with new ones. Only applicable for raw deployment mode.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ComponentImplementation">ComponentImplementation
</h3>
<div>
<p>ComponentImplementation interface is implemented by predictor, transformer, and explainer implementations</p>
</div>
<h3 id="serving.kserve.io/v1beta1.ComponentStatusSpec">ComponentStatusSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServiceStatus">InferenceServiceStatus</a>)
</p>
<div>
<p>ComponentStatusSpec describes the state of the component</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>latestReadyRevision</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Latest revision name that is in ready state</p>
</td>
</tr>
<tr>
<td>
<code>latestCreatedRevision</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Latest revision name that is created</p>
</td>
</tr>
<tr>
<td>
<code>previousRolledoutRevision</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Previous revision name that is rolled out with 100 percent traffic</p>
</td>
</tr>
<tr>
<td>
<code>latestRolledoutRevision</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Latest revision name that is rolled out with 100 percent traffic</p>
</td>
</tr>
<tr>
<td>
<code>traffic</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/serving/pkg/apis/serving/v1#TrafficTarget">
[]knative.dev/serving/pkg/apis/serving/v1.TrafficTarget
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Traffic holds the configured traffic distribution for latest ready revision and previous rolled out revision.</p>
</td>
</tr>
<tr>
<td>
<code>url</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>URL holds the primary url that will distribute traffic over the provided traffic targets.
This will be one the REST or gRPC endpoints that are available.
It generally has the form http[s]://{route-name}.{route-namespace}.{cluster-level-suffix}</p>
</td>
</tr>
<tr>
<td>
<code>restUrl</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>REST endpoint of the component if available.</p>
</td>
</tr>
<tr>
<td>
<code>grpcUrl</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>gRPC endpoint of the component if available.</p>
</td>
</tr>
<tr>
<td>
<code>address</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Addressable">
knative.dev/pkg/apis/duck/v1.Addressable
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Addressable endpoint for the InferenceService</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ComponentType">ComponentType
(<code>string</code> alias)</h3>
<div>
<p>ComponentType contains the different types of components of the service</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;explainer&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;predictor&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;transformer&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.CustomExplainer">CustomExplainer
</h3>
<div>
<p>CustomExplainer defines arguments for configuring a custom explainer.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podspec-v1-core">
Kubernetes core/v1.PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.CustomPredictor">CustomPredictor
</h3>
<div>
<p>CustomPredictor defines arguments for configuring a custom server.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podspec-v1-core">
Kubernetes core/v1.PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.CustomTransformer">CustomTransformer
</h3>
<div>
<p>CustomTransformer defines arguments for configuring a custom transformer.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podspec-v1-core">
Kubernetes core/v1.PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.DeployConfig">DeployConfig
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>defaultDeploymentMode</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ExplainerConfig">ExplainerConfig
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ExplainersConfig">ExplainersConfig</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>image</code><br/>
<em>
string
</em>
</td>
<td>
<p>explainer docker image name</p>
</td>
</tr>
<tr>
<td>
<code>defaultImageVersion</code><br/>
<em>
string
</em>
</td>
<td>
<p>default explainer docker image version</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ExplainerExtensionSpec">ExplainerExtensionSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ARTExplainerSpec">ARTExplainerSpec</a>)
</p>
<div>
<p>ExplainerExtensionSpec defines configuration shared across all explainer frameworks</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>storageUri</code><br/>
<em>
string
</em>
</td>
<td>
<p>The location of a trained explanation model</p>
</td>
</tr>
<tr>
<td>
<code>runtimeVersion</code><br/>
<em>
string
</em>
</td>
<td>
<p>Defaults to latest Explainer Version</p>
</td>
</tr>
<tr>
<td>
<code>config</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<p>Inline custom parameter settings for explainer</p>
</td>
</tr>
<tr>
<td>
<code>Container</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>
(Members of <code>Container</code> are embedded into this type.)
</p>
<em>(Optional)</em>
<p>Container enables overrides for the predictor.
Each framework will have different defaults that are populated in the underlying container spec.</p>
</td>
</tr>
<tr>
<td>
<code>storage</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.StorageSpec">
StorageSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Storage Spec for model location</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ExplainerSpec">ExplainerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServiceSpec">InferenceServiceSpec</a>)
</p>
<div>
<p>ExplainerSpec defines the container spec for a model explanation server,
The following fields follow a &ldquo;1-of&rdquo; semantic. Users must specify exactly one spec.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>art</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ARTExplainerSpec">
ARTExplainerSpec
</a>
</em>
</td>
<td>
<p>Spec for ART explainer</p>
</td>
</tr>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PodSpec">
PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
<p>This spec is dual purpose.
1) Users may choose to provide a full PodSpec for their custom explainer.
The field PodSpec.Containers is mutually exclusive with other explainers.
2) Users may choose to provide a Explainer and specify PodSpec
overrides in the PodSpec. They must not provide PodSpec.Containers in this case.</p>
</td>
</tr>
<tr>
<td>
<code>ComponentExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">
ComponentExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ComponentExtensionSpec</code> are embedded into this type.)
</p>
<p>Component extension defines the deployment configurations for explainer</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ExplainersConfig">ExplainersConfig
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServicesConfig">InferenceServicesConfig</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>art</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ExplainerConfig">
ExplainerConfig
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.FailureInfo">FailureInfo
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelStatus">ModelStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>location</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Name of component to which the failure relates (usually Pod name)</p>
</td>
</tr>
<tr>
<td>
<code>reason</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.FailureReason">
FailureReason
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>High level class of failure</p>
</td>
</tr>
<tr>
<td>
<code>message</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Detailed error message</p>
</td>
</tr>
<tr>
<td>
<code>modelRevisionName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Internal Revision/ID of model, tied to specific Spec contents</p>
</td>
</tr>
<tr>
<td>
<code>time</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#time-v1-meta">
Kubernetes meta/v1.Time
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Time failure occurred or was discovered</p>
</td>
</tr>
<tr>
<td>
<code>exitCode</code><br/>
<em>
int32
</em>
</td>
<td>
<em>(Optional)</em>
<p>Exit status from the last termination of the container</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.FailureReason">FailureReason
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.FailureInfo">FailureInfo</a>)
</p>
<div>
<p>FailureReason enum</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;InvalidPredictorSpec&#34;</p></td>
<td><p>The current Predictor Spec is invalid or unsupported</p>
</td>
</tr><tr><td><p>&#34;ModelLoadFailed&#34;</p></td>
<td><p>The model failed to load within a ServingRuntime container</p>
</td>
</tr><tr><td><p>&#34;NoSupportingRuntime&#34;</p></td>
<td><p>There are no ServingRuntime which support the specified model type</p>
</td>
</tr><tr><td><p>&#34;RuntimeDisabled&#34;</p></td>
<td><p>The ServingRuntime is disabled</p>
</td>
</tr><tr><td><p>&#34;RuntimeNotRecognized&#34;</p></td>
<td><p>There is no ServingRuntime defined with the specified runtime name</p>
</td>
</tr><tr><td><p>&#34;RuntimeUnhealthy&#34;</p></td>
<td><p>Corresponding ServingRuntime containers failed to start or are unhealthy</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.HuggingFaceRuntimeSpec">HuggingFaceRuntimeSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>HuggingFaceRuntimeSpec defines arguments for configuring HuggingFace model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.InferenceService">InferenceService
</h3>
<div>
<p>InferenceService is the Schema for the InferenceServices API</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>metadata</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#objectmeta-v1-meta">
Kubernetes meta/v1.ObjectMeta
</a>
</em>
</td>
<td>
Refer to the Kubernetes API documentation for the fields of the
<code>metadata</code> field.
</td>
</tr>
<tr>
<td>
<code>spec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.InferenceServiceSpec">
InferenceServiceSpec
</a>
</em>
</td>
<td>
<br/>
<br/>
<table>
<tr>
<td>
<code>predictor</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorSpec">
PredictorSpec
</a>
</em>
</td>
<td>
<p>Predictor defines the model serving spec</p>
</td>
</tr>
<tr>
<td>
<code>explainer</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ExplainerSpec">
ExplainerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Explainer defines the model explanation service spec,
explainer service calls to predictor or transformer if it is specified.</p>
</td>
</tr>
<tr>
<td>
<code>transformer</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TransformerSpec">
TransformerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Transformer defines the pre/post processing before and after the predictor call,
transformer service calls to predictor service.</p>
</td>
</tr>
</table>
</td>
</tr>
<tr>
<td>
<code>status</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.InferenceServiceStatus">
InferenceServiceStatus
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.InferenceServiceDefaulter">InferenceServiceDefaulter
</h3>
<div>
<p>InferenceServiceDefaulter is responsible for setting default values on the InferenceService
when created or updated.</p>
<p>NOTE: The +kubebuilder:object:generate=false and +k8s:deepcopy-gen=false marker prevents controller-gen from generating DeepCopy methods,
as it is used only for temporary operations and does not need to be deeply copied.</p>
</div>
<h3 id="serving.kserve.io/v1beta1.InferenceServiceSpec">InferenceServiceSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceService">InferenceService</a>)
</p>
<div>
<p>InferenceServiceSpec is the top level type for this resource</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>predictor</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorSpec">
PredictorSpec
</a>
</em>
</td>
<td>
<p>Predictor defines the model serving spec</p>
</td>
</tr>
<tr>
<td>
<code>explainer</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ExplainerSpec">
ExplainerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Explainer defines the model explanation service spec,
explainer service calls to predictor or transformer if it is specified.</p>
</td>
</tr>
<tr>
<td>
<code>transformer</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TransformerSpec">
TransformerSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Transformer defines the pre/post processing before and after the predictor call,
transformer service calls to predictor service.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.InferenceServiceStatus">InferenceServiceStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceService">InferenceService</a>)
</p>
<div>
<p>InferenceServiceStatus defines the observed state of InferenceService</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>Status</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Status">
knative.dev/pkg/apis/duck/v1.Status
</a>
</em>
</td>
<td>
<p>
(Members of <code>Status</code> are embedded into this type.)
</p>
<p>Conditions for the InferenceService <br/>
- PredictorReady: predictor readiness condition; <br/>
- TransformerReady: transformer readiness condition; <br/>
- ExplainerReady: explainer readiness condition; <br/>
- RoutesReady (serverless mode only): aggregated routing condition, i.e. endpoint readiness condition; <br/>
- LatestDeploymentReady (serverless mode only): aggregated configuration condition, i.e. latest deployment readiness condition; <br/>
- Ready: aggregated condition; <br/></p>
</td>
</tr>
<tr>
<td>
<code>address</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis/duck/v1#Addressable">
knative.dev/pkg/apis/duck/v1.Addressable
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Addressable endpoint for the InferenceService</p>
</td>
</tr>
<tr>
<td>
<code>url</code><br/>
<em>
<a href="https://pkg.go.dev/knative.dev/pkg/apis#URL">
knative.dev/pkg/apis.URL
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>URL holds the url that will distribute traffic over the provided traffic targets.
It generally has the form http[s]://{route-name}.{route-namespace}.{cluster-level-suffix}</p>
</td>
</tr>
<tr>
<td>
<code>components</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ComponentStatusSpec">
map[kserve.io/serving/pkg/apis/serving/v1beta1.ComponentType]kserve.io/serving/pkg/apis/serving/v1beta1.ComponentStatusSpec
</a>
</em>
</td>
<td>
<p>Statuses for the components of the InferenceService</p>
</td>
</tr>
<tr>
<td>
<code>modelStatus</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelStatus">
ModelStatus
</a>
</em>
</td>
<td>
<p>Model related statuses</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.InferenceServiceValidator">InferenceServiceValidator
</h3>
<div>
<p>InferenceServiceValidator is responsible for validating the InferenceService resource
when it is created, updated, or deleted.</p>
<p>NOTE: The +kubebuilder:object:generate=false and +k8s:deepcopy-gen=false marker prevents controller-gen from generating DeepCopy methods,
as this struct is used only for temporary operations and does not need to be deeply copied.</p>
</div>
<h3 id="serving.kserve.io/v1beta1.InferenceServicesConfig">InferenceServicesConfig
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>explainers</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ExplainersConfig">
ExplainersConfig
</a>
</em>
</td>
<td>
<p>Explainer configurations</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.IngressConfig">IngressConfig
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>ingressGateway</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>knativeLocalGatewayService</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>localGateway</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>localGatewayService</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>ingressDomain</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>ingressClassName</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>additionalIngressDomains</code><br/>
<em>
[]string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>domainTemplate</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>urlScheme</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>disableIstioVirtualHost</code><br/>
<em>
bool
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>pathTemplate</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>disableIngressCreation</code><br/>
<em>
bool
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.LightGBMSpec">LightGBMSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>LightGBMSpec defines arguments for configuring LightGBMSpec model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.LocalModelConfig">LocalModelConfig
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>enabled</code><br/>
<em>
bool
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>jobNamespace</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>defaultJobImage</code><br/>
<em>
string
</em>
</td>
<td>
</td>
</tr>
<tr>
<td>
<code>fsGroup</code><br/>
<em>
int64
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.LoggerSpec">LoggerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">ComponentExtensionSpec</a>)
</p>
<div>
<p>LoggerSpec specifies optional payload logging available for all components</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>url</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>URL to send logging events</p>
</td>
</tr>
<tr>
<td>
<code>mode</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.LoggerType">
LoggerType
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the scope of the loggers. <br />
Valid values are: <br />
- &ldquo;all&rdquo; (default): log both request and response; <br />
- &ldquo;request&rdquo;: log only request; <br />
- &ldquo;response&rdquo;: log only response <br /></p>
</td>
</tr>
<tr>
<td>
<code>metadataHeaders</code><br/>
<em>
[]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Matched metadata HTTP headers for propagating to inference logger cloud events.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.LoggerType">LoggerType
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.LoggerSpec">LoggerSpec</a>)
</p>
<div>
<p>LoggerType controls the scope of log publishing</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;all&#34;</p></td>
<td><p>LogAll Logger mode to log both request and response</p>
</td>
</tr><tr><td><p>&#34;request&#34;</p></td>
<td><p>LogRequest Logger mode to log only request</p>
</td>
</tr><tr><td><p>&#34;response&#34;</p></td>
<td><p>LogResponse Logger mode to log only response</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelCopies">ModelCopies
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelStatus">ModelStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>failedCopies</code><br/>
<em>
int
</em>
</td>
<td>
<p>How many copies of this predictor&rsquo;s models failed to load recently</p>
</td>
</tr>
<tr>
<td>
<code>totalCopies</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Total number copies of this predictor&rsquo;s models that are currently loaded</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelFormat">ModelFormat
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelSpec">ModelSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>name</code><br/>
<em>
string
</em>
</td>
<td>
<p>Name of the model format.</p>
</td>
</tr>
<tr>
<td>
<code>version</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Version of the model format.
Used in validating that a predictor is supported by a runtime.
Can be &ldquo;major&rdquo;, &ldquo;major.minor&rdquo; or &ldquo;major.minor.patch&rdquo;.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelRevisionStates">ModelRevisionStates
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelStatus">ModelStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>activeModelState</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelState">
ModelState
</a>
</em>
</td>
<td>
<p>High level state string: Pending, Standby, Loading, Loaded, FailedToLoad</p>
</td>
</tr>
<tr>
<td>
<code>targetModelState</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelState">
ModelState
</a>
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelSpec">ModelSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>modelFormat</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelFormat">
ModelFormat
</a>
</em>
</td>
<td>
<p>ModelFormat being served.</p>
</td>
</tr>
<tr>
<td>
<code>runtime</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specific ClusterServingRuntime/ServingRuntime name to use for deployment.</p>
</td>
</tr>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelState">ModelState
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelRevisionStates">ModelRevisionStates</a>)
</p>
<div>
<p>ModelState enum</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;FailedToLoad&#34;</p></td>
<td><p>All copies of the model failed to load</p>
</td>
</tr><tr><td><p>&#34;Loaded&#34;</p></td>
<td><p>At least one copy of the model is loaded</p>
</td>
</tr><tr><td><p>&#34;Loading&#34;</p></td>
<td><p>Model is loading</p>
</td>
</tr><tr><td><p>&#34;Pending&#34;</p></td>
<td><p>Model is not yet registered</p>
</td>
</tr><tr><td><p>&#34;Standby&#34;</p></td>
<td><p>Model is available but not loaded (will load when used)</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ModelStatus">ModelStatus
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServiceStatus">InferenceServiceStatus</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>transitionStatus</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TransitionStatus">
TransitionStatus
</a>
</em>
</td>
<td>
<p>Whether the available predictor endpoints reflect the current Spec or is in transition</p>
</td>
</tr>
<tr>
<td>
<code>states</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelRevisionStates">
ModelRevisionStates
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>State information of the predictor&rsquo;s model.</p>
</td>
</tr>
<tr>
<td>
<code>lastFailureInfo</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.FailureInfo">
FailureInfo
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Details of last failure, when load of target model is failed or blocked.</p>
</td>
</tr>
<tr>
<td>
<code>copies</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelCopies">
ModelCopies
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Model copy information of the predictor&rsquo;s model.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ONNXRuntimeSpec">ONNXRuntimeSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>ONNXRuntimeSpec defines arguments for configuring ONNX model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.PMMLSpec">PMMLSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>PMMLSpec defines arguments for configuring PMML model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.PaddleServerSpec">PaddleServerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.PodSpec">PodSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ExplainerSpec">ExplainerSpec</a>, <a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>, <a href="#serving.kserve.io/v1beta1.TransformerSpec">TransformerSpec</a>, <a href="#serving.kserve.io/v1beta1.WorkerSpec">WorkerSpec</a>)
</p>
<div>
<p>PodSpec is a description of a pod.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>volumes</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#volume-v1-core">
[]Kubernetes core/v1.Volume
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>List of volumes that can be mounted by containers belonging to the pod.
More info: <a href="https://kubernetes.io/docs/concepts/storage/volumes">https://kubernetes.io/docs/concepts/storage/volumes</a></p>
</td>
</tr>
<tr>
<td>
<code>initContainers</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
[]Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>List of initialization containers belonging to the pod.
Init containers are executed in order prior to containers being started. If any
init container fails, the pod is considered to have failed and is handled according
to its restartPolicy. The name for an init container or normal container must be
unique among all containers.
Init containers may not have Lifecycle actions, Readiness probes, Liveness probes, or Startup probes.
The resourceRequirements of an init container are taken into account during scheduling
by finding the highest request/limit for each resource type, and then using the max of
of that value or the sum of the normal containers. Limits are applied to init containers
in a similar fashion.
Init containers cannot currently be added or removed.
Cannot be updated.
More info: <a href="https://kubernetes.io/docs/concepts/workloads/pods/init-containers/">https://kubernetes.io/docs/concepts/workloads/pods/init-containers/</a></p>
</td>
</tr>
<tr>
<td>
<code>containers</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
[]Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>List of containers belonging to the pod.
Containers cannot currently be added or removed.
There must be at least one container in a Pod.
Cannot be updated.</p>
</td>
</tr>
<tr>
<td>
<code>ephemeralContainers</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#ephemeralcontainer-v1-core">
[]Kubernetes core/v1.EphemeralContainer
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>List of ephemeral containers run in this pod. Ephemeral containers may be run in an existing
pod to perform user-initiated actions such as debugging. This list cannot be specified when
creating a pod, and it cannot be modified by updating the pod spec. In order to add an
ephemeral container to an existing pod, use the pod&rsquo;s ephemeralcontainers subresource.
This field is beta-level and available on clusters that haven&rsquo;t disabled the EphemeralContainers feature gate.</p>
</td>
</tr>
<tr>
<td>
<code>restartPolicy</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#restartpolicy-v1-core">
Kubernetes core/v1.RestartPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Restart policy for all containers within the pod.
One of Always, OnFailure, Never.
Default to Always.
More info: <a href="https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#restart-policy">https://kubernetes.io/docs/concepts/workloads/pods/pod-lifecycle/#restart-policy</a></p>
</td>
</tr>
<tr>
<td>
<code>terminationGracePeriodSeconds</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional duration in seconds the pod needs to terminate gracefully. May be decreased in delete request.
Value must be non-negative integer. The value zero indicates stop immediately via
the kill signal (no opportunity to shut down).
If this value is nil, the default grace period will be used instead.
The grace period is the duration in seconds after the processes running in the pod are sent
a termination signal and the time when the processes are forcibly halted with a kill signal.
Set this value longer than the expected cleanup time for your process.
Defaults to 30 seconds.</p>
</td>
</tr>
<tr>
<td>
<code>activeDeadlineSeconds</code><br/>
<em>
int64
</em>
</td>
<td>
<em>(Optional)</em>
<p>Optional duration in seconds the pod may be active on the node relative to
StartTime before the system will actively try to mark it failed and kill associated containers.
Value must be a positive integer.</p>
</td>
</tr>
<tr>
<td>
<code>dnsPolicy</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#dnspolicy-v1-core">
Kubernetes core/v1.DNSPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Set DNS policy for the pod.
Defaults to &ldquo;ClusterFirst&rdquo;.
Valid values are &lsquo;ClusterFirstWithHostNet&rsquo;, &lsquo;ClusterFirst&rsquo;, &lsquo;Default&rsquo; or &lsquo;None&rsquo;.
DNS parameters given in DNSConfig will be merged with the policy selected with DNSPolicy.
To have DNS options set along with hostNetwork, you have to specify DNS policy
explicitly to &lsquo;ClusterFirstWithHostNet&rsquo;.</p>
</td>
</tr>
<tr>
<td>
<code>nodeSelector</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>NodeSelector is a selector which must be true for the pod to fit on a node.
Selector which must match a node&rsquo;s labels for the pod to be scheduled on that node.
More info: <a href="https://kubernetes.io/docs/concepts/configuration/assign-pod-node/">https://kubernetes.io/docs/concepts/configuration/assign-pod-node/</a></p>
</td>
</tr>
<tr>
<td>
<code>serviceAccountName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>ServiceAccountName is the name of the ServiceAccount to use to run this pod.
More info: <a href="https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/">https://kubernetes.io/docs/tasks/configure-pod-container/configure-service-account/</a></p>
</td>
</tr>
<tr>
<td>
<code>serviceAccount</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>DeprecatedServiceAccount is a depreciated alias for ServiceAccountName.
Deprecated: Use serviceAccountName instead.</p>
</td>
</tr>
<tr>
<td>
<code>automountServiceAccountToken</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>AutomountServiceAccountToken indicates whether a service account token should be automatically mounted.</p>
</td>
</tr>
<tr>
<td>
<code>nodeName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>NodeName is a request to schedule this pod onto a specific node. If it is non-empty,
the scheduler simply schedules this pod onto that node, assuming that it fits resource
requirements.</p>
</td>
</tr>
<tr>
<td>
<code>hostNetwork</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Host networking requested for this pod. Use the host&rsquo;s network namespace.
If this option is set, the ports that will be used must be specified.
Default to false.</p>
</td>
</tr>
<tr>
<td>
<code>hostPID</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Use the host&rsquo;s pid namespace.
Optional: Default to false.</p>
</td>
</tr>
<tr>
<td>
<code>hostIPC</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Use the host&rsquo;s ipc namespace.
Optional: Default to false.</p>
</td>
</tr>
<tr>
<td>
<code>shareProcessNamespace</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Share a single process namespace between all of the containers in a pod.
When this is set containers will be able to view and signal processes from other containers
in the same pod, and the first process in each container will not be assigned PID 1.
HostPID and ShareProcessNamespace cannot both be set.
Optional: Default to false.</p>
</td>
</tr>
<tr>
<td>
<code>securityContext</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podsecuritycontext-v1-core">
Kubernetes core/v1.PodSecurityContext
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>SecurityContext holds pod-level security attributes and common container settings.
Optional: Defaults to empty.  See type description for default values of each field.</p>
</td>
</tr>
<tr>
<td>
<code>imagePullSecrets</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#localobjectreference-v1-core">
[]Kubernetes core/v1.LocalObjectReference
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ImagePullSecrets is an optional list of references to secrets in the same namespace to use for pulling any of the images used by this PodSpec.
If specified, these secrets will be passed to individual puller implementations for them to use. For example,
in the case of docker, only DockerConfig type secrets are honored.
More info: <a href="https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod">https://kubernetes.io/docs/concepts/containers/images#specifying-imagepullsecrets-on-a-pod</a></p>
</td>
</tr>
<tr>
<td>
<code>hostname</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the hostname of the Pod
If not specified, the pod&rsquo;s hostname will be set to a system-defined value.</p>
</td>
</tr>
<tr>
<td>
<code>subdomain</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the fully qualified Pod hostname will be &ldquo;<hostname>.<subdomain>.<pod namespace>.svc.<cluster domain>&rdquo;.
If not specified, the pod will not have a domainname at all.</p>
</td>
</tr>
<tr>
<td>
<code>affinity</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#affinity-v1-core">
Kubernetes core/v1.Affinity
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the pod&rsquo;s scheduling constraints</p>
</td>
</tr>
<tr>
<td>
<code>schedulerName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the pod will be dispatched by specified scheduler.
If not specified, the pod will be dispatched by default scheduler.</p>
</td>
</tr>
<tr>
<td>
<code>tolerations</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#toleration-v1-core">
[]Kubernetes core/v1.Toleration
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, the pod&rsquo;s tolerations.</p>
</td>
</tr>
<tr>
<td>
<code>hostAliases</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#hostalias-v1-core">
[]Kubernetes core/v1.HostAlias
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>HostAliases is an optional list of hosts and IPs that will be injected into the pod&rsquo;s hosts
file if specified. This is only valid for non-hostNetwork pods.</p>
</td>
</tr>
<tr>
<td>
<code>priorityClassName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, indicates the pod&rsquo;s priority. &ldquo;system-node-critical&rdquo; and
&ldquo;system-cluster-critical&rdquo; are two special keywords which indicate the
highest priorities with the former being the highest priority. Any other
name must be defined by creating a PriorityClass object with that name.
If not specified, the pod priority will be default or zero if there is no
default.</p>
</td>
</tr>
<tr>
<td>
<code>priority</code><br/>
<em>
int32
</em>
</td>
<td>
<em>(Optional)</em>
<p>The priority value. Various system components use this field to find the
priority of the pod. When Priority Admission Controller is enabled, it
prevents users from setting this field. The admission controller populates
this field from PriorityClassName.
The higher the value, the higher the priority.</p>
</td>
</tr>
<tr>
<td>
<code>dnsConfig</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#poddnsconfig-v1-core">
Kubernetes core/v1.PodDNSConfig
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the DNS parameters of a pod.
Parameters specified here will be merged to the generated DNS
configuration based on DNSPolicy.</p>
</td>
</tr>
<tr>
<td>
<code>readinessGates</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podreadinessgate-v1-core">
[]Kubernetes core/v1.PodReadinessGate
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>If specified, all readiness gates will be evaluated for pod readiness.
A pod is ready when all its containers are ready AND
all conditions specified in the readiness gates have status equal to &ldquo;True&rdquo;
More info: <a href="https://git.k8s.io/enhancements/keps/sig-network/580-pod-readiness-gates">https://git.k8s.io/enhancements/keps/sig-network/580-pod-readiness-gates</a></p>
</td>
</tr>
<tr>
<td>
<code>runtimeClassName</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>RuntimeClassName refers to a RuntimeClass object in the node.k8s.io group, which should be used
to run this pod.  If no RuntimeClass resource matches the named class, the pod will not be run.
If unset or empty, the &ldquo;legacy&rdquo; RuntimeClass will be used, which is an implicit class with an
empty definition that uses the default runtime handler.
More info: <a href="https://git.k8s.io/enhancements/keps/sig-node/585-runtime-class">https://git.k8s.io/enhancements/keps/sig-node/585-runtime-class</a>
This is a beta feature as of Kubernetes v1.14.</p>
</td>
</tr>
<tr>
<td>
<code>enableServiceLinks</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>EnableServiceLinks indicates whether information about services should be injected into pod&rsquo;s
environment variables, matching the syntax of Docker links.
Optional: Defaults to true.</p>
</td>
</tr>
<tr>
<td>
<code>preemptionPolicy</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#preemptionpolicy-v1-core">
Kubernetes core/v1.PreemptionPolicy
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>PreemptionPolicy is the Policy for preempting pods with lower priority.
One of Never, PreemptLowerPriority.
Defaults to PreemptLowerPriority if unset.
This field is beta-level, gated by the NonPreemptingPriority feature-gate.</p>
</td>
</tr>
<tr>
<td>
<code>overhead</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#resourcelist-v1-core">
Kubernetes core/v1.ResourceList
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Overhead represents the resource overhead associated with running a pod for a given RuntimeClass.
This field will be autopopulated at admission time by the RuntimeClass admission controller. If
the RuntimeClass admission controller is enabled, overhead must not be set in Pod create requests.
The RuntimeClass admission controller will reject Pod create requests which have the overhead already
set. If RuntimeClass is configured and selected in the PodSpec, Overhead will be set to the value
defined in the corresponding RuntimeClass, otherwise it will remain unset and treated as zero.
More info: <a href="https://git.k8s.io/enhancements/keps/sig-node/688-pod-overhead/README.md">https://git.k8s.io/enhancements/keps/sig-node/688-pod-overhead/README.md</a>
This field is beta-level as of Kubernetes v1.18, and is only honored by servers that enable the PodOverhead feature.</p>
</td>
</tr>
<tr>
<td>
<code>topologySpreadConstraints</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#topologyspreadconstraint-v1-core">
[]Kubernetes core/v1.TopologySpreadConstraint
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>TopologySpreadConstraints describes how a group of pods ought to spread across topology
domains. Scheduler will schedule pods in a way which abides by the constraints.
All topologySpreadConstraints are ANDed.</p>
</td>
</tr>
<tr>
<td>
<code>setHostnameAsFQDN</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>If true the pod&rsquo;s hostname will be configured as the pod&rsquo;s FQDN, rather than the leaf name (the default).
In Linux containers, this means setting the FQDN in the hostname field of the kernel (the nodename field of struct utsname).
In Windows containers, this means setting the registry value of hostname for the registry key HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Tcpip\Parameters to FQDN.
If a pod does not have FQDN, this has no effect.
Default to false.</p>
</td>
</tr>
<tr>
<td>
<code>os</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podos-v1-core">
Kubernetes core/v1.PodOS
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Specifies the OS of the containers in the pod.
Some pod and container fields are restricted if this is set.</p>
<p>If the OS field is set to linux, the following fields must be unset:
-securityContext.windowsOptions</p>
<p>If the OS field is set to windows, following fields must be unset:
- spec.hostPID
- spec.hostIPC
- spec.securityContext.seLinuxOptions
- spec.securityContext.seccompProfile
- spec.securityContext.fsGroup
- spec.securityContext.fsGroupChangePolicy
- spec.securityContext.sysctls
- spec.shareProcessNamespace
- spec.securityContext.runAsUser
- spec.securityContext.runAsGroup
- spec.securityContext.supplementalGroups
- spec.containers[<em>].securityContext.seLinuxOptions
- spec.containers[</em>].securityContext.seccompProfile
- spec.containers[<em>].securityContext.capabilities
- spec.containers[</em>].securityContext.readOnlyRootFilesystem
- spec.containers[<em>].securityContext.privileged
- spec.containers[</em>].securityContext.allowPrivilegeEscalation
- spec.containers[<em>].securityContext.procMount
- spec.containers[</em>].securityContext.runAsUser
- spec.containers[*].securityContext.runAsGroup
This is an alpha field and requires the IdentifyPodOS feature</p>
</td>
</tr>
<tr>
<td>
<code>hostUsers</code><br/>
<em>
bool
</em>
</td>
<td>
<em>(Optional)</em>
<p>Use the host&rsquo;s user namespace.
Optional: Default to true.
If set to true or not present, the pod will be run in the host user namespace, useful
for when the pod needs a feature only available to the host user namespace, such as
loading a kernel module with CAP_SYS_MODULE.
When set to false, a new userns is created for the pod. Setting false is useful for
mitigating container breakout vulnerabilities even allowing users to run their
containers as root without actually having root privileges on the host.
This field is alpha-level and is only honored by servers that enable the UserNamespacesSupport feature.</p>
</td>
</tr>
<tr>
<td>
<code>schedulingGates</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podschedulinggate-v1-core">
[]Kubernetes core/v1.PodSchedulingGate
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>SchedulingGates is an opaque list of values that if specified will block scheduling the pod.
If schedulingGates is not empty, the pod will stay in the SchedulingGated state and the
scheduler will not attempt to schedule the pod.</p>
<p>SchedulingGates can only be set at pod creation time, and be removed only afterwards.</p>
<p>This is a beta feature enabled by the PodSchedulingReadiness feature gate.</p>
</td>
</tr>
<tr>
<td>
<code>resourceClaims</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#podresourceclaim-v1-core">
[]Kubernetes core/v1.PodResourceClaim
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>ResourceClaims defines which ResourceClaims must be allocated
and reserved before the Pod is allowed to start. The resources
will be made available to those containers which consume them
by name.</p>
<p>This is an alpha field and requires enabling the
DynamicResourceAllocation feature gate.</p>
<p>This field is immutable.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.PredictorExtensionSpec">PredictorExtensionSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.HuggingFaceRuntimeSpec">HuggingFaceRuntimeSpec</a>, <a href="#serving.kserve.io/v1beta1.LightGBMSpec">LightGBMSpec</a>, <a href="#serving.kserve.io/v1beta1.ModelSpec">ModelSpec</a>, <a href="#serving.kserve.io/v1beta1.ONNXRuntimeSpec">ONNXRuntimeSpec</a>, <a href="#serving.kserve.io/v1beta1.PMMLSpec">PMMLSpec</a>, <a href="#serving.kserve.io/v1beta1.PaddleServerSpec">PaddleServerSpec</a>, <a href="#serving.kserve.io/v1beta1.SKLearnSpec">SKLearnSpec</a>, <a href="#serving.kserve.io/v1beta1.TFServingSpec">TFServingSpec</a>, <a href="#serving.kserve.io/v1beta1.TorchServeSpec">TorchServeSpec</a>, <a href="#serving.kserve.io/v1beta1.TritonSpec">TritonSpec</a>, <a href="#serving.kserve.io/v1beta1.XGBoostSpec">XGBoostSpec</a>)
</p>
<div>
<p>PredictorExtensionSpec defines configuration shared across all predictor frameworks</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>storageUri</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>This field points to the location of the trained model which is mounted onto the pod.</p>
</td>
</tr>
<tr>
<td>
<code>runtimeVersion</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Runtime version of the predictor docker image</p>
</td>
</tr>
<tr>
<td>
<code>protocolVersion</code><br/>
<em>
github.com/kserve/kserve/pkg/constants.InferenceServiceProtocol
</em>
</td>
<td>
<em>(Optional)</em>
<p>Protocol version to use by the predictor (i.e. v1 or v2 or grpc-v1 or grpc-v2)</p>
</td>
</tr>
<tr>
<td>
<code>Container</code><br/>
<em>
<a href="https://kubernetes.io/docs/reference/generated/kubernetes-api/v1.25/#container-v1-core">
Kubernetes core/v1.Container
</a>
</em>
</td>
<td>
<p>
(Members of <code>Container</code> are embedded into this type.)
</p>
<em>(Optional)</em>
<p>Container enables overrides for the predictor.
Each framework will have different defaults that are populated in the underlying container spec.</p>
</td>
</tr>
<tr>
<td>
<code>storage</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.StorageSpec">
StorageSpec
</a>
</em>
</td>
<td>
<em>(Optional)</em>
<p>Storage Spec for model location</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.PredictorImplementation">PredictorImplementation
</h3>
<div>
<p>PredictorImplementation defines common functions for all predictors e.g Tensorflow, Triton, etc</p>
</div>
<h3 id="serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServiceSpec">InferenceServiceSpec</a>)
</p>
<div>
<p>PredictorSpec defines the configuration for a predictor,
The following fields follow a &ldquo;1-of&rdquo; semantic. Users must specify exactly one spec.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>sklearn</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.SKLearnSpec">
SKLearnSpec
</a>
</em>
</td>
<td>
<p>Spec for SKLearn model server</p>
</td>
</tr>
<tr>
<td>
<code>xgboost</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.XGBoostSpec">
XGBoostSpec
</a>
</em>
</td>
<td>
<p>Spec for XGBoost model server</p>
</td>
</tr>
<tr>
<td>
<code>tensorflow</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TFServingSpec">
TFServingSpec
</a>
</em>
</td>
<td>
<p>Spec for TFServing (<a href="https://github.com/tensorflow/serving">https://github.com/tensorflow/serving</a>)</p>
</td>
</tr>
<tr>
<td>
<code>pytorch</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TorchServeSpec">
TorchServeSpec
</a>
</em>
</td>
<td>
<p>Spec for TorchServe (<a href="https://pytorch.org/serve">https://pytorch.org/serve</a>)</p>
</td>
</tr>
<tr>
<td>
<code>triton</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.TritonSpec">
TritonSpec
</a>
</em>
</td>
<td>
<p>Spec for Triton Inference Server (<a href="https://github.com/triton-inference-server/server">https://github.com/triton-inference-server/server</a>)</p>
</td>
</tr>
<tr>
<td>
<code>onnx</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ONNXRuntimeSpec">
ONNXRuntimeSpec
</a>
</em>
</td>
<td>
<p>Spec for ONNX runtime (<a href="https://github.com/microsoft/onnxruntime">https://github.com/microsoft/onnxruntime</a>)</p>
</td>
</tr>
<tr>
<td>
<code>huggingface</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.HuggingFaceRuntimeSpec">
HuggingFaceRuntimeSpec
</a>
</em>
</td>
<td>
<p>Spec for HuggingFace runtime (<a href="https://github.com/huggingface">https://github.com/huggingface</a>)</p>
</td>
</tr>
<tr>
<td>
<code>pmml</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PMMLSpec">
PMMLSpec
</a>
</em>
</td>
<td>
<p>Spec for PMML (<a href="http://dmg.org/pmml/v4-1/GeneralStructure.html">http://dmg.org/pmml/v4-1/GeneralStructure.html</a>)</p>
</td>
</tr>
<tr>
<td>
<code>lightgbm</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.LightGBMSpec">
LightGBMSpec
</a>
</em>
</td>
<td>
<p>Spec for LightGBM model server</p>
</td>
</tr>
<tr>
<td>
<code>paddle</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PaddleServerSpec">
PaddleServerSpec
</a>
</em>
</td>
<td>
<p>Spec for Paddle model server (<a href="https://github.com/PaddlePaddle/Serving">https://github.com/PaddlePaddle/Serving</a>)</p>
</td>
</tr>
<tr>
<td>
<code>model</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ModelSpec">
ModelSpec
</a>
</em>
</td>
<td>
<p>Model spec for any arbitrary framework.</p>
</td>
</tr>
<tr>
<td>
<code>workerSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.WorkerSpec">
WorkerSpec
</a>
</em>
</td>
<td>
<p>WorkerSpec for enabling multi-node/multi-gpu</p>
</td>
</tr>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PodSpec">
PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
<p>This spec is dual purpose. <br />
1) Provide a full PodSpec for custom predictor.
The field PodSpec.Containers is mutually exclusive with other predictors (i.e. TFServing). <br />
2) Provide a predictor (i.e. TFServing) and specify PodSpec
overrides, you must not provide PodSpec.Containers in this case. <br /></p>
</td>
</tr>
<tr>
<td>
<code>ComponentExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">
ComponentExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ComponentExtensionSpec</code> are embedded into this type.)
</p>
<p>Component extension defines the deployment configurations for a predictor</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.SKLearnSpec">SKLearnSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>SKLearnSpec defines arguments for configuring SKLearn model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.ScaleMetric">ScaleMetric
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">ComponentExtensionSpec</a>)
</p>
<div>
<p>ScaleMetric enum</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;cpu&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;concurrency&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;memory&#34;</p></td>
<td></td>
</tr><tr><td><p>&#34;rps&#34;</p></td>
<td></td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.SecurityConfig">SecurityConfig
</h3>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>autoMountServiceAccountToken</code><br/>
<em>
bool
</em>
</td>
<td>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.StorageSpec">StorageSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ExplainerExtensionSpec">ExplainerExtensionSpec</a>, <a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">PredictorExtensionSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>path</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The path to the model object in the storage. It cannot co-exist
with the storageURI.</p>
</td>
</tr>
<tr>
<td>
<code>schemaPath</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The path to the model schema file in the storage.</p>
</td>
</tr>
<tr>
<td>
<code>parameters</code><br/>
<em>
map[string]string
</em>
</td>
<td>
<em>(Optional)</em>
<p>Parameters to override the default storage credentials and config.</p>
</td>
</tr>
<tr>
<td>
<code>key</code><br/>
<em>
string
</em>
</td>
<td>
<em>(Optional)</em>
<p>The Storage Key in the secret for this model.</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.TFServingSpec">TFServingSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>TFServingSpec defines arguments for configuring Tensorflow model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.TorchServeSpec">TorchServeSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>TorchServeSpec defines arguments for configuring PyTorch model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.TransformerSpec">TransformerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.InferenceServiceSpec">InferenceServiceSpec</a>)
</p>
<div>
<p>TransformerSpec defines transformer service for pre/post processing</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PodSpec">
PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
<p>This spec is dual purpose. <br />
1) Provide a full PodSpec for custom transformer.
The field PodSpec.Containers is mutually exclusive with other transformers. <br />
2) Provide a transformer and specify PodSpec
overrides, you must not provide PodSpec.Containers in this case. <br /></p>
</td>
</tr>
<tr>
<td>
<code>ComponentExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.ComponentExtensionSpec">
ComponentExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>ComponentExtensionSpec</code> are embedded into this type.)
</p>
<p>Component extension defines the deployment configurations for a transformer</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.TransitionStatus">TransitionStatus
(<code>string</code> alias)</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.ModelStatus">ModelStatus</a>)
</p>
<div>
<p>TransitionStatus enum</p>
</div>
<table>
<thead>
<tr>
<th>Value</th>
<th>Description</th>
</tr>
</thead>
<tbody><tr><td><p>&#34;BlockedByFailedLoad&#34;</p></td>
<td><p>Target model failed to load</p>
</td>
</tr><tr><td><p>&#34;InProgress&#34;</p></td>
<td><p>Waiting for target model to reach state of active model</p>
</td>
</tr><tr><td><p>&#34;InvalidSpec&#34;</p></td>
<td><p>Target predictor spec failed validation</p>
</td>
</tr><tr><td><p>&#34;UpToDate&#34;</p></td>
<td><p>Predictor is up-to-date (reflects current spec)</p>
</td>
</tr></tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.TritonSpec">TritonSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>TritonSpec defines arguments for configuring Triton model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.WorkerSpec">WorkerSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PodSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PodSpec">
PodSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PodSpec</code> are embedded into this type.)
</p>
</td>
</tr>
<tr>
<td>
<code>size</code><br/>
<em>
int
</em>
</td>
<td>
<em>(Optional)</em>
<p>Configure the number of replicas in the worker set, each worker set represents the unit of scaling</p>
</td>
</tr>
</tbody>
</table>
<h3 id="serving.kserve.io/v1beta1.XGBoostSpec">XGBoostSpec
</h3>
<p>
(<em>Appears on:</em><a href="#serving.kserve.io/v1beta1.PredictorSpec">PredictorSpec</a>)
</p>
<div>
<p>XGBoostSpec defines arguments for configuring XGBoost model serving.</p>
</div>
<table>
<thead>
<tr>
<th>Field</th>
<th>Description</th>
</tr>
</thead>
<tbody>
<tr>
<td>
<code>PredictorExtensionSpec</code><br/>
<em>
<a href="#serving.kserve.io/v1beta1.PredictorExtensionSpec">
PredictorExtensionSpec
</a>
</em>
</td>
<td>
<p>
(Members of <code>PredictorExtensionSpec</code> are embedded into this type.)
</p>
<p>Contains fields shared across all predictors</p>
</td>
</tr>
</tbody>
</table>
<hr/>
<p><em>
Generated with <code>gen-crd-api-reference-docs</code>
on git commit <code>7e436424</code>.
</em></p>
