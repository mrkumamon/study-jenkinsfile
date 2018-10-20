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
