pipeline{
    agent any
    stages{
        stage("Build"){
            steps{
                echo "building docker image"
                bat "docker build -t myapp ."
            }
        }
        stage("Docker login"){
            steps{
                bat "docker login -u swathi1276 -p Docker@123"
            }
        }
        stage("Push image to dockerhub"){
            steps{
                bat "docker tag myapp:latest swathi1276/demo:latest"
                bat "docker push swathi1276/demo:latest"
            }
        }
        stage("deploy to kubernetes"){
            steps{
                bat "kubectl apply -f deployment.yaml --validate=false"
                bat "kubectl apply -f service.yaml"
            }
        }
    }
    post{
        success{
            echo "pipeline executed successfully"
        }
        failure{
            echo "pipeline failed, check the logs"
        }
    }
}