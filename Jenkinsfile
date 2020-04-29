pipeline {
    agent any
    tools {
        maven 'maven3.6.1' 
    }
    stages {
        stage('Build') { 
            steps {
                sh 'mvn -B -DskipTests clean package' 
            }
        }
        stage('Test') {
            steps {
                sh 'echo test'
            }
            post {
                always {
                    sh 'echo post1'
                }
            }
        }
        stage('Deliver') {
            steps {
                withCredentials([usernameColonPassword(credentialsId: 'gitpush', variable: 'gpr')]) {
                    sh 'git fetch --all'
          sh 'git checkout master'             
    sh 'git commit -am "Merged develop branch to master'
    sh 'git push origin master'
}
            }
        }
    }
}
