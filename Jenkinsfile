
pipeline {
 agent any
 stages {
        stage('Build') { 
       
          steps {
           def scmUrl = scm.getUserRemoteConfigs()[0].getUrl()
           sh 'echo ${scmUrl}'
           sh 'ls'
           sh 'git branch'
checkout([$class: 'GitSCM', branches: [[name: '*/feature']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'PreBuildMerge', options: [mergeRemote: 'origin', mergeTarget: 'master']]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git']]])
           sh 'git branch'
           sh 'git checkout master'
           sh 'git pull '
           sh 'git merge origin/feature'
         
           sh 'ls'
          
   //     sh 'GIT_REPO_URL = null'
    //       sh 'command = "grep -oP '{?<=url>[^<]+}' /var/lib/jenkins/jobs/${JOB_NAME}/config.xml" '
    //    sh 'GIT_REPO_URL = sh(returnStdout: true, script: command).trim(); '
    //   sh  'echo "Detected Git Repo URL: ${GIT_REPO_URL}" ' 
    
          
           //sh 'git commit -am "jenkins commit"'
           //sh 'git push'
           withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'pass', usernameVariable: 'name')]) {
            sh 'git push https://${name}:${pass}@github.com/padmarajugadam/gitpublish.git'
           }
          }
         
        }
 }
}
