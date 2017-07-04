pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/dkdeploy/example-dkdeploy-typo3-cms']]])
            }
        }
        stage('Test') {
            steps {
                echo 'Testing..'
                docker.image('maven:3.3.3-jdk-8').inside {
                  echo 'Inside Maven'
                  sh 'mvn -B clean install'
                }
            }
        }
        stage('Deploy') {
            steps {
                echo 'Deploying....'
            }
        }
    }
}