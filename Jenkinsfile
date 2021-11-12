node{
   stage('SCM Checkout'){
       git  url: 'https://github.com/SuhithJayasekara/demo'
   }
   
   stage('Build Docker Image'){
     sh 'docker build -t 34341755/my-app:2.0.0 .'
   }
   stage('Push Docker Image'){
    
        sh "docker login -u 34341755 -p 34341755suhith"
     
        sh 'docker push 34341755/my-app:2.0.0'
   }
   stage('Run Container on Dev Server'){
     def dockerRun = 'docker run -p 80:80 -d --name my-app 34341755/my-app:2.0.0'
     sshagent(['suhith-docker']) {
       sh "ssh -o StrictHostKeyChecking=no ec2-user@44.192.99.10 ${dockerRun}"
     }
   }
}
