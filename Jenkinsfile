pipeline {
    agent any
   // tools {
      //add tool
   //   maven 'maven3.6.1' 
  //  }
    stages {
        //stage('Build') { 
       //     steps {
         //       sh 'mvn -B -DskipTests clean package' 
         //   }
       // }
        //stage('Test') {
         //   steps {
          //      sh 'echo test'
          //  }
           // post {
           //     always {
             //       sh 'echo post1'
             //   }
           // }
      //  }
        stage('Deliver') {
            steps {
                
                git credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git'
                git branch: 'feature', credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git'
                
                
               withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'git-pass', usernameVariable: 'git-user')]) {
                   sh 'git checkout origin/master'
                  sh 'git merge origin/feature'
                  //  sh 'ls -lrt'
                 //   sh 'git branch'
                    
                  sh 'git commit -am "default commit"'
                  sh 'git push https://padmarajugadam:Vijuchinna35@github.com/padmarajugadam/gitpublish.git'
     }
          
                
               
                    
                     
   

            }
        }
    }
}
