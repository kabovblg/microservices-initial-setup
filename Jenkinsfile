node {
    stage('Checkout') {
        checkout([$class: 'GitSCM',
            branches: [[name: '*/main']],
            extensions: [],
            userRemoteConfigs: [[credentialsId: 'git',
            url: 'https://github.com/kabovblg/microservices-initial-setup.git']]])
    }
    stage('Deploy') {
        step([$class: 'KubernetesEngineBuilder',
            projectId: env.PROJECT_ID,
            clusterName: env.CLUSTER,
            location: env.ZONE,
            manifestPattern: 'kubernetes/',
            credentialsId: env.PROJECT_ID,
            verifyDeployments: true])
    }
}