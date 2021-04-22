pipeline {
    agent { label 'slave1' }
    parameters {
      choice choices: ['1, 2, 3, 4'], description: '', name: 'test'
        
    }
    stages {
      stage('Checking out the source code') {
        steps {
          git credentialsId: 'github', url: 'https://github.com/Vivek-linuxx/Website_demo.git'
        }
      }
      stage ('Building the source code') {
          steps {
              sh 'mvn install'
          }
      post {
        success {
          deploy adapters: [tomcat9(credentialsId: 'war_deployer_user', path: '', url: 'http://172.31.92.144:8080')], contextPath: 'petclinic', onFailure: false, war: '**/*.war'
  }
}
      }
    }

