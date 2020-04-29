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
                withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'git-pass', usernameVariable: 'git-user')]) {
   
                    sh 'git checkout master'
                    sh 'git push https://${git-user}:${git-pass}@github.com/padmarajugadam/gitpublish.git'
     }
          
                
               
                    
                     
   

            }
        }
    }
}
