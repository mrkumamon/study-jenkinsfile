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
