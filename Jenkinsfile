pipeline {
 agent any
 stages {
      stage('build')   {
			     steps {
				      echo 'I am executing stage 1
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
