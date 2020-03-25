pipeline {
   agent any
   stages {
      stage('Git Checkout') {
         steps {
            ws('/var/lib/jenkins/workspace/multi') {
           checkout([$class: 'GitSCM', branches: scm.branches, extensions:scm.extensions + [[$class: 'dev'], [$class: 'WipeWorkspace']], doGenerateSubmoduleConfigurations: false, submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Deeps333/maven-modular.git']]])
         }
             }
      }
      stage ('Build Approval')
        {steps {
            build 'Build Approval'
        }      }

         stage ('Build')
         { steps { 
             build 'Buildmodular'
         }       }

         stage ('Deploy SIT')
         { steps {
             build 'DeploySITmodular'
         }       }
   
         
   }}
         
         
