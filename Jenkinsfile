
pipeline {
 agent any
 stages {
        stage('Build') { 
          steps {
           sh 'ls'
           sh 'git branch'
checkout([$class: 'GitSCM', branches: [[name: '*/feature']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'PreBuildMerge', options: [mergeRemote: 'origin', mergeTarget: 'master']]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git']]])
           sh 'git branch'
           sh 'git checkout master'
           sh 'git pull '
           sh 'git merge origin/feature'
         
           sh 'ls'
           try{
        GIT_REPO_URL = null
        command = "grep -oP '(?<=url>)[^<]+' /var/lib/jenkins/jobs/${JOB_NAME}/config.xml"
        GIT_REPO_URL = sh(returnStdout: true, script: command).trim();
        echo "Detected Git Repo URL: ${GIT_REPO_URL}"  
    }
           catch(err){
        throw err
        error "Colud not find any Git repository for the job ${JOB_NAME}"
  }
           //sh 'git commit -am "jenkins commit"'
           //sh 'git push'
           withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'pass', usernameVariable: 'name')]) {
            sh 'git push https://${name}:${pass}@github.com/padmarajugadam/gitpublish.git'
           }
          }
         
        }
 }
}
