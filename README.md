# Jenkins Helm Chart

Here i have customized the values.yaml file to update the service port to 8085 so the jenkins should be available on port 8085 instead of default port


## Installing the Chart

To install the chart jenkins, simply follow the below steps:

1. Ensure the Helm Client and Helm Tiller pod is running on your kubernetes cluster.

Run helm version to check whether the helm and tiller(server) are running well before proceeding to next steps.

$helm version
Client: &version.Version{SemVer:"v2.14.3", GitCommit:"0e7f3b6637f7af8fcfddb3d2941fcc7cbebb0085", GitTreeState:"clean"}
Server: &version.Version{SemVer:"v2.14.3", GitCommit:"0e7f3b6637f7af8fcfddb3d2941fcc7cbebb0085", GitTreeState:"clean"}

2. Clone the repo https://github.com/angautam/helm-chart-jenkins.git on your machine where helm client is running.

3. Then run below command : 

helm install --name jenkins-releasev1 helm-chart-jenkins


You can watch the status of by running 'kubectl get svc --namespace default -w jenkins-releasev1'

  export SERVICE_IP=$(kubectl get svc --namespace default jenkins-releasev1 --template "{{ range (index .status.loadBalancer.ingress 0) }}{{ . }}{{ end }}")
  
  echo http://$SERVICE_IP:8085/login




