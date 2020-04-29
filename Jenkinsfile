pipeline {
 agent any
 stages {
        stage('Build') { 
          steps {
           sh 'ls'
           sh 'git branch'
checkout([$class: 'GitSCM', branches: [[name: '*/feature']], doGenerateSubmoduleConfigurations: false, extensions: [[$class: 'PreBuildMerge', options: [mergeRemote: 'origin', mergeTarget: 'master']]], submoduleCfg: [], userRemoteConfigs: [[credentialsId: 'gitpush', url: 'https://github.com/padmarajugadam/gitpublish.git']]])
         sh 'git merge origin/feature origin/master'
          sh 'git checkout origin/master'
           sh 'ls'
          }
        }
 }
}
