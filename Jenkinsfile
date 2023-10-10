pipeline {
    agent {
        label 'maven'
    }
	tools {
        // Install the Maven version configured as "M3" and add it to the path.
        maven "maven"
        
    }
    
	//environment {	
	//	DOCKERHUB_CREDENTIALS=credentials('dockerloginid')
	//} 
    
    stages {
        stage('SCM Checkout') {
            steps {
                // Get some code from a GitHub repository
                git 'https://github.com/peraboinaajay/Java-mvn-app2.git'
            }
		}
        stage('Maven Build') {
            steps {
                // Run Maven on a Unix agent.
                sh "mvn -Dmaven.test.failure.ignore=true clean package"
            }
		}
        stage("Docker build"){
            steps {
				 sh 'docker build -t ajayperaboina/java-docker-hub .'
            }
        }
         stage('Login') {
            steps {
              sh 'echo "Peraboin@85" | docker login -u ajayperaboina --password-stdin'
            }
       }
        stage('Push') {
            steps {
               sh 'docker push ajayperaboina/java-docker-hub'
            }
        }
    // stage('Deploy') {
    //   steps {
    //     sh 'kubectl apply -f deploy.yaml'
    //   }
    // }
    }  
        post {
           always {
               sh 'docker logout'
            }
        }


	///stage('Login') {

	//		steps {
	//			sh 'echo "Peraboin@85" | docker login -u ajayperaboina --password-stdin'
	//		}
	//	}
      //  stage('Approve - push Image to dockerhub'){
       //     steps{
                
                //----------------send an approval prompt-------------
        //        script {
          //         env.APPROVED_DEPLOY = input message: 'User input required Choose "yes" | "Abort"'
            //           }
                //-----------------end approval prompt------------
            //}
        //}
		//stage('Push2DockerHub') {

		//	steps {
		//		sh "docker push loksaieta/loksai-eta-app:latest"
		//	}
		//}
        //stage('Approve - Deployment to Kubernetes Cluster'){
          //  steps{
                
                //----------------send an approval prompt-----------
            //    script {
              //     env.APPROVED_DEPLOY = input message: 'User input required Choose "yes" | "Abort"'
                //       }
                //-----------------end approval prompt------------
            //}
        //}
        //stage('Deploy to Kubernetes Cluster') {
          //  steps {
		//script {
		//sshPublisher(publishers: [sshPublisherDesc(configName: 'kubernetescluster', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'kubectl apply -f k8smvndeployment.yaml', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '.', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '*.yaml')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
		//}
          //  }
	

}
