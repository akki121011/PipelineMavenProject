pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Build Started'
		sh 'mvn clean package'
                sh 'pwd'
                sh 'whoami'
                sh "docker build -t webapp:${env.BUILD_ID} ."
                sh 'docker login -u akashgupta123 -p Password@123'
                sh "docker tag webapp:${env.BUILD_ID} akashgupta123/webapp:${env.BUILD_ID}"
                sh "docker push akashgupta123/webapp:${env.BUILD_ID}"
		   
                }
            post{
                success{
                    echo 'Done'
                    echo 'Archeiving Artifact'
                    archiveArtifacts '**/*.war'
                    }
                }
            }
        stage('Deploy to staging'){
            steps{
                echo 'Deploying to staging server'
		echo 'Removed deploy to staging'
            }
            post{
                success{
                    echo 'Deployed'
                }
                failure{
                    echo 'Recheck code'
                }
            }
        }
        }
    }

