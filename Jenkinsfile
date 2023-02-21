pipeline{
    agent any 
    stages{
        stage("checkout"){
            steps{
                git url: "https://github.com/akshay451995/djpipeline.git"
            }
        }
        stage("build image from Dockerfile"){
            steps{
                script{
                    sh "docker build -t akshay451995/myimage ."
                }
            }
        }
        stage("login and push the image to dockerhub"){
            steps{
                script{
                    withCredentials([string(credentialsId: 'dockerhubp', variable: 'dockerhubp')]) {
                    sh "docker login -u akshay451995 -p ${dockerhubp}"
}
                    sh "docker push akshay451995/myimage"
                }
            }
        }
        stage("pull the image from dockerhub"){
            steps{
                script{
                    sh "docker pull akshay451995/myimage"
                }
            }
        }
        stage("build container from the image"){
            steps{
                script{
                    sh "docker run -dit --name container1 akshay451995/myimage"
                }
            }
        }
    }
}
