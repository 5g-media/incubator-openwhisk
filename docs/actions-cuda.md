<!--
#
# Licensed to the Apache Software Foundation (ASF) under one or more
# contributor license agreements.  See the NOTICE file distributed with
# this work for additional information regarding copyright ownership.
# The ASF licenses this file to You under the Apache License, Version 2.0
# (the "License"); you may not use this file except in compliance with
# the License.  You may obtain a copy of the License at
#
#     http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.
#
-->

## Creating and invoking Cuda actions

The following section guides you through creating and invoking a single Cuda action.

Cuda actions are executed using Cuda 8.0 on Ubuntu 16.04. [Cuda runtime repository](https://github.com/5g-media/incubator-openwhisk-runtime-cuda.git).

These actions are executed using Cuda-toolkit [8.0](https://developer.nvidia.com/cuda-80-ga2-download-archive). You will need
a compatible version of the compiler locally available to generate the executable. Without Cuda-toolkit compiler,
you cannot create an OpenWhisk action.

To use the Cuda runtime, you must [deploy Openwhisk on Kubernetes](https://github.com/5g-media/incubator-openwhisk-deploy-kube/tree/cuda-v0.1) which is already configured to use this runtime. Your GPU nodes will have to get labeled with the name of `kind` excluding
none-alphanumeric values e.g. cuda8:

```shell
$kubectl label nodes <GPU_NODE_NAME> cuda:8=true
```

You should specify the `wsk` CLI parameter `--kind` when creating or updating an action. The available Cuda kinds are:

* Cuda 8.0: `--kind cuda:8@selector`

## Packaging Cuda actions in zip files

Cuda actions accept initialization data via a (zip) file, similar to other actions kinds.

  ```shell
  ~/wsk -i action create cuda_Test ~/myAction.zip --kind cuda:8@selector
  ```

