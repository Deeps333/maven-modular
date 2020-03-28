pipeline {
   agent any
   stages {
      stage('Git Checkout') {
         steps {
            ws('/var/lib/jenkins/workspace/multimodularws') {
           
           checkout([$class: 'GitSCM', branches: [[name: '*/dev']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[refspec: '+refs/heads/master:refs/remotes/origin/master +refs/heads/dev:refs/remotes/origin/dev', url: 'https://github.com/Deeps333/maven-modular.git']]])
           
          }
             }
      }
      stage ('Build Approval')
        {steps {
            build 'Build Approval'
        }      }

         stage ('Build')
         { steps { 
             build 'multimodularbuild'
         }       }

         stage ('Deploy SIT')
         { steps {
             build 'deploysitmultimodular'
         }       }
   
         
   }}
         
         
