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


try, catch finally
```
try {
    sh 'exit 1'
}
catch (exc) {
    error 'Something failed, I should sound the klaxons!'
}
```
