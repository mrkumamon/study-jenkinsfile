node {
    stage('Test Baidu') {
        sh "curl baidu.com"
        print("BuildResult="+currentBuild.result)
        sh "exit 1"
    }
    stage('Deploy') {
      stage('Deploy') {
      print("BuildResult="+currentBuild.result)
      if (currentBuild.result == null || currentBuild.result == 'SUCCESS') {
              sh 'echo publishing.......'
          }
      }
    }
}
