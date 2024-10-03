node ('agent1'){
    def app
    stage('Cloning Git'){
        chekout scm
    }
    stage('Build-and-Tag'){
        app = docker.build("sbnvglm/sudoku")
    }
    stage('Post-to-dockerhub'){
        docker.withRegitsry('https://registry.hub.docker.com', 'dockerhub_creds'){
            app.push("latest")
        }
    }
    stage('Push-image-server'){
        sh "docker-compose down"
        sh "docker-compose up -d"
    }
}
