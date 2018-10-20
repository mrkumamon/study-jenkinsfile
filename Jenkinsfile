#!/usr/bin/env groovy
def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello Mr. ${username}"

node {
    stage('Test Baidu') {
        sh "curl baidu.com"
    }
    stage('Deploy') {
      stage('Deploy') {
      print("BuildResult="+currentBuild.result)
      if (currentBuild.result == null || currentBuild.result == 'SUCCESS') {
              sh "echo publishing to.......${username}"
          }
      }
      echo "${env.BUILD_ID} on ${env.JENKINS_URL} is complete"
    }
}
