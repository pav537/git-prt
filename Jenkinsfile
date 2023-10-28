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

     stage('create nodeport service')
        {
          steps {
            sh "sudo kubectl create -f k8s.yml"
          }
        }

    }
  
}
