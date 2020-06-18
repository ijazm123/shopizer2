pipeline{
    agent any
    stages{
     stage('git checkout'){
      steps{
       git 'https://github.com/balucc/shopizer.git'
}}
       stage('Build'){
     steps{
       sh label: '', script: './mvnw clean install'
      }}
        stage('Docker image build'){
            steps{
              sshPublisher(publishers: [sshPublisherDesc(configName: 'docker-server', transfers: [sshTransfer(cleanRemote: false, excludes: '', execCommand: 'cp sm-shop/Dockerfile . ;docker build . -t shopizer ; docker run -itd --name shopizer-container -p 8080:8081 shopizer', execTimeout: 120000, flatten: false, makeEmptyDirs: false, noDefaultExcludes: false, patternSeparator: '[, ]+', remoteDirectory: '', remoteDirectorySDF: false, removePrefix: '', sourceFiles: '**/**')], usePromotionTimestamp: false, useWorkspaceInPromotion: false, verbose: false)])
            }}
    }}
