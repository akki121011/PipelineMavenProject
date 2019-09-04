pipeline{
    agent any
    tools{
        maven 'localMaven'
    }
    stages{
        stage('Build'){
            steps{
                echo 'Build Started'
		bat label: '', script: 'mvn clean package'
                }
            post{
                success{
                    echo 'Done'
                    }
                }
            }
        }
    }

