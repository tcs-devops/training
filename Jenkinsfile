node{
        stage('Build'){
            echo 'Starting to build the app. This is a scripted pipeline'
        }
        stage('Test'){
            input 'Do you want to proceed?'
        }
        stage('Deploy'){
            stage('Deploy start'){
                echo 'Start the deploy'
            }
            stage('Deploying now'){
                agent{any{
                    reuseNode true
                }}
                echo 'Docker created'
            }
        }
}
