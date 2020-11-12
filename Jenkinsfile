//CODE_CHANGES = getGitChanges()

pipeline {
    agent any //여기서 시작
    
    tools {
        maven 'jenkins-maven'
    }
    
    environment {
        NAME = 'nodeman'
        LASTNAME = 'JAY'
        secret = credentials('SECRET_TEST')
    }
    
    parameters {
        string(name: 'TEST', defaultValue: '0', description: '')
        choice(name: 'VERSION', choices: ['1.1', '1.2', '1.3'], description: '' )
        booleanParam(name: 'BUILD', defaultValue: true, description: '')
    }
    
    stages {
        stage('Build/Test') {
			//when {
			//		expression {
			//				BRANCH_NAME == 'master' || CODE_CHANGES == true
			//		}
			//}
			when {
				expression {
						params.TEST
				}
			}
            steps {
                echo 'Building..'
                echo 'deploy version: ${params.TEST}'
                sh '''
                    echo "hey here!!!!"
                    ls -alh
                '''
								//sh 'npm install'
								//sh 'npm build'
            }
        }
        stage('Harbor Check') {
            steps {
                sh 'mvn -version'
                echo 'Harbor Check...'
            }   
        }
		stage('Package') {
			steps {
					echo 'Package..'
            //retry(3) {
            //    sh 'asdf'
            //}
            //timeout(time: 3, unit: 'SECONDS') {
            //    sh 'sleep 5'
            //}
			}
		}   
        stage('Push') { 
            steps {
                echo 'Push...'
            }   
        }
        stage('Deploy') {
            steps {
                //echo 'Deploying..'
                sh 'echo ${NAME} ${LASTNAME} ${secret}'
                //sh 'echo "Fail!"; exit 1'
                
                //withCredentials([usernamePassword(credentialsId: 'UsernamePassCredential', usernameVariable: 'USERNAME', passwordVariable: 'PASSWORD')]) {
                //    sh 'some script ${USERNAME} ${PASSWORD}'
                //}
            }
        }
		stage('Pod Check') {
		 
	        steps {
				echo 'Pod Check...'
		    }
		   
			
		}
    }
    post {
        always {
            echo 'always'
        }
        success {
            echo 'success'
        }
        failure {
            echo 'failure'
        }
        unstable {
            echo 'unstable'
        }
    }
}

node {
	//groovy script
}