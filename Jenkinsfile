pipeline {
    agent any
    parameters {
        string(name: 'company_parameter', defaultValue: 'dkd', description: 'The company the pipeline runs in')
    }
    environment {
            GREETINGS_TO = 'Jenkins Techlab'
            JENKINS_URL = 'platform_example'
        }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
            }
        }
        stage('Test') {
            steps {
                sh "echo \"Running ${env.BUILD_ID} on ${env.JENKINS_URL}\" in company ${params.company_parameter}"
            }
        }
        stage('Deploy') {
            steps {
                echo "Hello, ${env.GREETINGS_TO} !"

                // also available as env variable to a process:
                sh 'echo "Hello, $GREETINGS_TO !"'

                script {
                    def pipelineType = 'declarative'
                    echo "yeah we executed a script within the ${pipelineType} pipeline"
                }
            }
        }
    }
}