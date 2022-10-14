pipeline {
  agent any
  stages {
    stage('Git Branch') {
      steps {
        echo "$GIT_BRANCH"
      }
    }
    stage('Initialize') {
      steps {
        script{
          def dockerHome = tool 'docker'
          env.PATH = "${dockerHome}/bin:${env.PATH}"
        }
      }
    }
    stage('Docker Build') {
      steps {
        sh(script: """
          cd azure-vote/
          docker images -a
          docker build -t jenkins-pipeline .
          docker images -a
          cd ..
        """)
      }
    }
  }
}
