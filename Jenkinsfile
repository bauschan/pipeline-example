pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
      }
    }
    stage('Test') {
      steps {
        parallel(
          "Test": {
            sh '"echo "Running ${env.BUILD_ID} on ${env.JENKINS_URL}" in company ${params.company_parameter}"'
            
          },
          "Unix": {
            isUnix()
            
          }
        )
      }
    }
    stage('Deploy') {
      steps {
        echo '"Hello, ${env.GREETINGS_TO} !"'
        sh 'echo "Hello, $GREETINGS_TO !"'
        script {
          def pipelineType = 'declarative'
          echo "yeah we executed a script within the ${pipelineType} pipeline"
        }
        
      }
    }
  }
  environment {
    GREETINGS_TO = 'TYPO3 Developer Days 2017'
    JENKINS_URL = 'platform_example'
  }
  parameters {
    string(name: 'company_parameter', defaultValue: 'dkd', description: 'The company the pipeline runs in')
  }
}