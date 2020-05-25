node{

    stage('SCM Checkout')
    {
        git credentialsId: '2ecc532c-fd96-4a70-9d95-58f4ce5a2c25', url: 'https://github.com/karthiksdv/online_shop.git'
    }
    
    stage('Run Docker Compose File')
    {
        sh 'docker-compose build'
        sh 'docker-compose up -d'
    }
    stage('PUSH image to Docker Hub')
    {
        withCredentials([string(credentialsId: 'DockerHubPassword', variable: 'DHPWD')]) 
        {
            sh "docker login -u karthiksdv -p ${DHPWD}"
        }
        sh 'docker push karthiksdv/phpmysql_app'
    }
}

