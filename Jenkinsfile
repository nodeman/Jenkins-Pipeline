pipeline {
    agent any //여기서 시작
    
    environment {
        NAME = 'nodeman'
        LASTNAME = 'JAY'
        //secret = credentials('SECRET_TEST')
    }
    
    stages {
        stage('Build') {
            steps {
                echo 'Building..'
                sh '''
                    echo "hey here!!!!"
                    ls -alh
                '''
								//sh 'npm install'
								//sh 'npm build'
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
                sh 'echo $NAME $LASTNAME'
                //sh 'echo "Fail!"; exit 1'
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