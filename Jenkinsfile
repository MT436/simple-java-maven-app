pipeline {
    agent any

    stages {
        stage('Git') {
            steps {
                git 'https://github.com/MT436/hello-world.git'
            }
        }
    stage('Build') {
            steps {
                sh 'mvn clean package'
            }
        }
     stage('Test') {
            steps {
                sh 'mvn test'
            }
            post {
                always {
                    junit '*/target/surefire-reports/*.xml'
                }
            }
        }
        stage('Deploy') {
            steps {
            deploy adapters: [tomcat9(credentialsId: 'tomcat1', path: '', url: 'http://65.0.251.201:8081')], contextPath: null, war: '**/*.war'
            }
        }
      
     }
}

