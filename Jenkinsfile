pipeline {
    agent any
    parameters {
        string(name: 'company_parameter', defaultValue: 'dkd', description: 'The company the pipeline runs in')
    }
    environment {
            GREETINGS_TO = 'Jenkins Techlab'
            JENKINS_URL = 'platform_example'
            RVM_HOME = tool('rvm')
        }
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/dkdeploy/example-dkdeploy-typo3-cms']]])
                sh  """#!/bin/bash
                    source \${RVM_HOME}/scripts/rvm
                    rvm use --install 2.3.4
                    gem list '^bundler\$' -i || gem install bundler
                    ruby --version
                    bundle --version
                """
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