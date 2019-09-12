node("docker") {
    docker.withRegistry('https://registry.hub.docker.com', 'docker-hub-credentials') {
    
        git url: "https://github.com/anjalirean/jenkin/", credentialsId: 'anjalirean'
    
        sh "git rev-parse HEAD > .git/anjalirean"
        def commit_id = readFile('.git/anjalirean').trim()
        println commit_id
    
        stage "build"
        def app = docker.build "aqua"
    
        stage "publish"
        app.push 'master'
        app.push "${commit_id}"
    }
}
