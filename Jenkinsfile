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
	 stage('quality') { 
            steps {
                sh 'mvn sonar:sonar' 
            }
        }
	  stage("Quality Gate"){
		  steps {
          timeout(time: 1, unit: 'HOURS') {
              def qg = waitForQualityGate()
              if (qg.status != 'OK') {
                  error "Pipeline aborted due to quality gate failure: ${qg.status}"
              }
          }
      }
	  }
      
        }						   

    post {
        
        success {
            sh ''' git branch
           git checkout master
           git pull 
          git merge origin/feature'''
    
           withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'pass', usernameVariable: 'name')]) {
            sh 'git push https://${name}:${pass}@github.com/padmarajugadam/gitpublish.git'
           }
        }
	 failure {
            echo 'I failed :('
        }
    }
}
