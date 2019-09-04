pipeline{
    agent any
    tools{
	    jdk 'localJDK'
        maven 'localMaven'
    }
    stages{
        stage('Build'){
            steps{
                echo 'Build Started'
		sh label: '', script: 'mvn clean package'
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
                deploy adapters: [tomcat8(credentialsId: 'a9809649-6d45-48cb-9203-56ce0c62cb97', path: '', url: 'http://localhost:8089')], contextPath: null, war: '**/*.war'
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

