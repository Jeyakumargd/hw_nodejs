node {
    environment{
    registry = "jeyakumargd/hw_nodejs"
    registryCredential = 'docker-hub-credentials'
    }

    stage('Clone repository') {
        checkout scm
    }

    stage('Build image') {
        app = docker.build(registry)
    }

    stage('Test image') {
        app.inside {
            sh 'echo "Tests passed"'
        }
    }

    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', registryCredential ) {
            dockerImage.push()
        }
    }
}
