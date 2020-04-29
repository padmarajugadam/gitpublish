pipeline {
 agent any
 stages {
        stage('Build') { 
          steps {
           sh 'ls'
           sh 'git branch'
checkout([$class: 'GitSCM', branches: [[name: '*/feature']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'PreBuildMerge', options: [mergeRemote: 'origin', mergeTarget: 'master']]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git']]])
           sh 'git checkout origin/master'
           sh 'git merge origin/feature '
         
           sh 'ls'
          }
          {
         withCredentials([usernamePassword(credentialsId: 'gitpush', passwordVariable: 'git-pass', usernameVariable: 'git-user')]) {

                    sh 'git checkout master'
                    sh 'git push https://${padmarajugadam}:${Vijuchinna35}@github.com/padmarajugadam/gitpublish.git'

         }
         }
        }
 }
}
