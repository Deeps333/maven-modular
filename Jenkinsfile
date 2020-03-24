pipeline {
   agent any
	options {
             skipDefaultCheckout true
	}
       stages {
      stage('Git Checkout') {
         steps {
           checkout([$class: 'GitSCM', branches: [[name: '*/master']], doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], userRemoteConfigs: [[url: 'https://github.com/Deeps333/maven-modular.git']]])
		}
	}
	stage ('Build')
	   
	    {steps{
                sh '/usr/share/maven/bin/mvn clean package -Dmaven.test.skip=true'
	    }    }
        stage ('Update the Version')
		{ steps {
          sh 'git checkout -b release/v2.0.0'      
          sh '/usr/share/maven/bin/mvn --batch-mode release:clean release:prepare release:perform -DreleaseVersion-2.0.0 -DdevelopmentVersion-2.0.1-SNAPSHOT -Dmaven.test.skip=true'
	        sh 'sudo git commit -m "Updated pom" pom.xml'

                sh 'sudo git push https://Deeps333:Deepanshu333@github.com/Deeps333/maven-modular.git HEAD:master'

                sh 'sudo git push https://Deeps333:Deepanshu333@github.com/Deeps333/maven-modular.git HEAD:dev'

                }       }
      }
          
   }
