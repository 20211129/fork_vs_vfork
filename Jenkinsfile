node {
    def app
    stage('Clone repository') {
        git 'https://github.com/jwpark-sungshin/fork_vs_vfork.git'
    }
    stage('Build image') {
        app = docker.build("yr20211129/test")
    }
    stage('Test image') {
        app.inside {
            sh 'make test'
        }
    }
    stage('Push image') {
        docker.withRegistry('https://registry.hub.docker.com', 'yr20211129') {
           app.push("${env.BUILD_NUMBER}")
           app.push("latest")
        }
    }
}
