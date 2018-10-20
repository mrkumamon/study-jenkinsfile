#!/usr/bin/env groovy
def username = 'Jenkins'
echo 'Hello Mr. ${username}'
echo "I said, Hello Mr. ${username}"

node {

    withEnv(["whoami=GabrielWu","second=2","third=3"]){
      echo "what's ${env.whoami}, what's ${env.second}, what's ${env.third}"
    }
    stage('scripted 01') {
      // if(env.whoami=="GabrielWu"){
      //   echo "this whoami = ${env.whoami}"
      // }else{
      //   echo "this whoami = not sure"
      // }
      //
      try {
          sh 'exit 1'
      }
      catch (exc) {
          warn 'this is warn'
      }finally{
        echo "this is fine"
      }

      try {
          sh 'exit 1'
      }
      catch (exc) {
          error 'Something failed, I should sound the klaxons!'
      }

      try {
          sh 'exit 1'
      }
      catch (exc) {
          warm 'this is warm'
      }finally{
        echo "this is fine"
      }
    }

    stage('Test Baidu') {
        sh "curl baidu.com"
        sh "echo Let me introduce ${env.whoami}"
    }
    stage('Deploy') {
      stage('Deploy') {
      print("BuildResult="+currentBuild.result)
      if (currentBuild.result == null || currentBuild.result == 'SUCCESS') {
              sh "echo publishing to.......${username}"
          }
      }
      echo "Build Id ${env.BUILD_ID} on ${env.JENKINS_URL} is complete"
    }
}
