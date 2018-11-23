node {
    stage('init') {
        checkout scm
    }

    stage('build') {
        acrQuickTask azureCredentialsId: '438bf5b7-50d9-413d-876f-1f2ad7b1c650', 
            imageNames: [[image: 'latest']], 
            registryName: 'jiesheacr', 
            resourceGroupName: 'jiesheacr', 
            dockerfile: 'samples/java/getting-started/webfrontend/Dockerfile.develop',
    }

    stage('deploy') {
        devSpaces aksName: 'jiesheaks', 
            azureCredentialsId: '438bf5b7-50d9-413d-876f-1f2ad7b1c650', 
            endpointVariable: '', 
            helmChartLocation: 'samples/java/getting-started/webfrontend/charts/webfrontend', 
            imageRepository: 'jieshe/ads-private', 
            imageTag: 'latest', 
            kubeconfigId: 'adskubeconfig', 
            resourceGroupName: 'jiesheaks', 
            secretName: 'registrysecret', 
            secretNamespace: 'jieshe', 
            sharedSpaceName: 'default', 
            spaceName: 'jieshe',
            dockerCredentials: [[credentialsId: 'dockerhub']]
    }
}