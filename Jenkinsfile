//def workspace = "pipeline_nexus"
pipeline {
    agent any
    tools {
    maven 'Maven-3.8.6'
    }
      stages {
	 stage('Build') {
            steps {

		sh 'mvn clean install'				
		}
        }
      //  stage('Build') {
       //     steps {
       //         script {
	//		    try {
	//				slackSend channel: '#grupo2', color: 'good', message: "Start job: ${BRANCH_NAME} ${JOB_NAME} ${BUILD_NUMBER} SUCCESS"
	//				echo 'Build'
	//				sh 'mvn clean install'
	//			}
	//    catch(all) {
	//		slackSend channel: '#grupo2', color: 'danger', message: "Fail job: ${BRANCH_NAME} ${JOB_NAME} ${BUILD_NUMBER} FAIL"
	//	}
	//		}	
	//	}
       // }
      //  stage('Sonar') {
        //    steps {
       //          script {      
	//			withSonarQubeEnv('Sonar') {
	//			sh 'mvn clean package sonar:sonar -Dsonar.projectKey=lab-04 -Dsonar.java.binaries=build'
       //            }
       //         }
       //     }
       // }
	//stage("Publish to Nexus Repository Manager") {
       //     steps {
       //         script {
       //            nexusPublisher nexusInstanceId: 'Nexus-Repository', nexusRepositoryId: 'devops-usach-nexus', 
	//		packages: [[$class: 'MavenPackage', mavenAssetList: [[classifier: '', extension: '', filePath: "${WORKSPACE}/build/DevOpsUsach2020-0.0.1.jar"]],
	//	        mavenCoordinate: [artifactId: 'DevOpsUsach2020', groupId: 'com.devopsusach2020', packaging: 'jar', version: "1.1.${BUILD_NUMBER}"]]]
       //         }
       //     }
      //  }  
	//stage('Pull the file off Nexus'){
       //    steps{
       //     withCredentials([usernameColonPassword(credentialsId: 'nexus', variable: 'NEXUS_CREDENTIALS')]){
       //         sh script: 'curl -u ${NEXUS_CREDENTIALS} -o DevOpsUsach2020-0.0.1.jar "http://nexus:8081/repository/devops-usach-nexus/com/devopsusach2020/DevOpsUsach2020/0.0.1/DevOpsUsach2020-0.0.1.jar"'
        //    }
        //  }
               
        //}  
	      
	stage('git push') {
		    steps {
			withCredentials([
			    gitUsernamePassword(credentialsId: 'Github', gitToolName: 'Default')
			]) {
			   	sh 'git config --global user.email "mabel.contreras182@gmail.com"'
  				sh 'git config --global user.name "Mabel Contreras"'
				
				sh 'git tag -a "Release1.0.${BUILD_NUMBER}" -m "V1.0.${BUILD_NUMBER}"'
				sh 'git merge origin/develop'
				sh 'git commit -am "Merged develop branch to main'
				sh "git push main"
			}
		    }
		}
        stage('Clean Workspace') {
            steps {
               cleanWs()
            }
        }
    }
}
