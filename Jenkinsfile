pipeline {
    agent {
        docker
        { 
            image 'mcr.microsoft.com/playwright:v1.59.1-noble'
            args '-u=root --entrypoint='
        }  
    }
    parameters {
        choice(name: 'test', choices: ['navigateur', 'tags',], description: 'Chosissez un navigateur')
        booleanParam(name: 'lancer', defaultValue: true, description: 'Lancertous les test')
        booleanParam(name: '', defaultValue: true, description: 'Lancer tous les test')
    }

    stages {
        stage('installe dependance'){
            steps{
                sh 'npm install'
            }
        }
        stage('lancer le deuxieme collection') {
                steps {
                
                sh'npx playwright test'
                }
        }
    }
}