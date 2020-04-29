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
           sh 'git commit -am "jenkins commit"'
           sh 'git push'
            sh 'git push https://padmarajugadam:Vijuchinna35@github.com/padmarajugadam/gitpublish.git origin master'
          }
         
        }
 }
}
