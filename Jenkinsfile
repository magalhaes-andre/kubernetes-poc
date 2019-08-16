pipeline{
    agent any
    parameters{
        string(name: 'gitCredential')
    }

    stages {
        stage ('Cleansing'){
            steps{
                cleanWs()
            }
        }

        stage ('Pulling From SCM'){
            steps{
                git branch: 'tema_18',
                credentialsId: "${params.gitCredential}",
                url: 'https://github.com/magalhaes-andre/jts.devops.2019.1'
            }
        }
        
        stage ('Applying kubernetes_scripts/ from SCM'){
            steps{
                dir("andre-magalhaes/tema_18/"){
                    sh "kubectl apply -f kubernetes_scripts/"
                }

            }
        }
    }
}