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
