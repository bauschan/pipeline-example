pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        echo 'Building..'
        archiveArtifacts 'workspace'
      }
    }
    stage('Test') {
      steps {
        sh '"echo \"Running ${env.BUILD_ID} on ${env.JENKINS_URL}\" in company ${params.company_parameter}"'
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
    GREETINGS_TO = 'Jenkins Techlab'
    JENKINS_URL = 'platform_example'
    RVM_HOME = tool('rvm')
  }
  parameters {
    string(name: 'company_parameter', defaultValue: 'dkd', description: 'The company the pipeline runs in')
  }
}