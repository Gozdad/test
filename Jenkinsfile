pipeline{
  agent any
  stages{
    stage("build"){
      steps{
        echo 'building the application ...'
      }
    }
    stage("test"){
      steps{
        echo 'testing the application ...'
      }
    }
    stage("deploy"){
      steps{
        echo 'deploying the application ...'
      }
    }
    stage('Publish artefacts') {
      steps {
        withCredentials([
          usernamePassword(credentialsId: JENKINS_GITHUB_CREDENTIALS_ID, usernameVariable: "GIT_USERNAME", passwordVariable: "GIT_PASSWORD")
        ]) {
          sh """
            git config --local credential.helper "!f() { echo username='${GIT_USERNAME}'; echo password='${GIT_PASSWORD}'; }; f"
            git config --local user.name '${GIT_USERNAME}'
            git config --local user.email '${GIT_USERNAME}@example.tld'
            make docs-publish
          """
        }
      }
    }
  }
}
