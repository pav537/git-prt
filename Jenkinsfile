#!groovy
pipeline{
  agent {label "master"}
  
    stages
      {
        stage('Docker Build') 
         {
    	      steps 
           {
      	     print("building docker image") 
             sh "sudo chmod 777 /var/run/docker.sock"
             sh "docker build -t pav537/2824:latest ."
      }
    }
        stage('docker push')
         {
            steps
           {
            withDockerRegistry([ credentialsId: "dockerhub", url: "" ]) {
            dockerImage.push()
              }
            }
         }

     stage('create nodeport service')
        {
          steps {
            sh "kubectl create -f k8s.yml"
          }
        }

    }
  
}
