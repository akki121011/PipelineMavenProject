pipeline{
    agent any
    stages{
        stage('Build'){
            steps{
                echo 'Hello world'
            }
            post{
                success{
                    echo 'Done'
                }
            }
        }
    }
}