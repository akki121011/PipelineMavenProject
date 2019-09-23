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
                deploy adapters: [tomcat8(credentialsId: 'a9809649-6d45-48cb-9203-56ce0c62cb97', path: '', url: 'http://localhost:8089')], contextPath: null, onFailure: false, war: '**/*.war'
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

