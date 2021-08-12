node{
   stage('SCM Checkout'){
       git branch: 'main', url: 'https://github.com/juned171/docker_node.git'
   }
    stage('Build Docker Image'){
     sh 'docker build -t juned171/newimage . '
   }
    stage('Push Docker Image'){
    withCredentials([string(credentialsId: 'docker-pwd', variable: 'dockerHubPwd')]) {
    sh "docker login -u juned171 -p ${dockerHubPwd}"
}
   sh 'docker push juned171/newimage'
    }
    
    stage('Run Container on Dev Server'){
        sh 'docker run -p 91:92 -d juned171/newimage'
    }
    
}
