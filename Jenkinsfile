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
        }
    }

