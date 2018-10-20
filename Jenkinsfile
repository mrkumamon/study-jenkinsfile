node {
    stage('Test Baidu') {
        sh "curl baidu.com"
    }
    stage('Deploy') {
      stage('Deploy') {
      print("BuildResult="+currentBuild.result)
      if (currentBuild.result == null || currentBuild.result == 'SUCCESS') {
              sh 'make publish'
          }
      }
    }
}
