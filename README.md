# setup jenkins in gcp
```
use username/password and add kubernetes plugin after install jenkins
https://cloud.google.com/solutions/configuring-jenkins-kubernetes-engine
https://cloud.google.com/solutions/jenkins-on-kubernetes-engine
```

# how to configure kubernetes plugin
```
find the cluster
CA: Get CA from  .kube/config then base64 -D
Server: there's server in .kube/config
authentication token:
$ kubectl get secrets -n kube-system
Get any one secret.
$ kubectl get secret $SECRET_NAME -n=kube-system -o json | jq -r '.data["token"]' | base64 -D > ~/user_token.txt
```

# sign in dashboard.
```
$ kubectl get secrets -n kube-system
Get any one secret.
$ kubectl get secret $SECRET_NAME -n=kube-system -o json | jq -r '.data["token"]' | base64 -D > ~/user_token.txt
then
run kubectl proxy
 http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
```

# start jenkins
```
docker run -u root --rm -d --name jenkins -p 8080:8080 -p 50000:50000 -p 8000:80 -p 4430:443 -v jenkins-data:/var/jenkins_home -v /var/run/docker.sock:/var/run/docker.sock jenkinsci/blueocean
```

# study-jenkinsfile

because jenkinsfile is at the root of project, so it can make and archive the project.
```
node {
    stage('Build') {
        sh 'make'
        archiveArtifacts artifacts: '**/target/*.jar', fingerprint: true
    }
}
```

it's better always use single quota and you can reference it within double quote
```
def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello Mr. ${username}"
```
"env." you can find all jenkins environment variables. All jenkins variable can be found at  <jenkins url>:8080/pipeline-syntax/globals#env
define custom environment variables.
```

An environment directive used in the top-level pipeline block will apply to all steps within the Pipeline.
An environment directive defined within a stage will only apply the given environment variables to steps within the stage.

```
withEnv, you must set a body, like {} and the env is not persisted out of the body
```
withEnv(["whoami=GabrielWu","second=2","third=3"]){
  echo "what's ${env.whoami}, what's ${env.second}, what's ${env.third}"
}
```
Scripted Pipeline is serially executed from the top of a Jenkinsfile downwards, like most traditional scripts in Groovy or other languages. Providing flow control therefore rests on Groovy expressions, such as the if/else conditionals, for example:
1: 从上到下执行。


try, catch finally。 Use 'error' instead of 'throw', 'throw' is not gonna work
```
try {
    sh 'exit 1'
}
catch (exc) {
    error 'Something failed, I should sound the klaxons!'
}
```
