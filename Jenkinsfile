pipeline {
    agent {
        docker
        { 
            image 'mcr.microsoft.com/playwright:v1.61.1-noble'
            args '-u=root --entrypoint='
        }  
    }
    parameters {
        choice(name: 'navigateur', choices: ['chromium', 'firefox','webkit'], description: 'Chosissez un navigateur')
        booleanParam(name: 'lancer', defaultValue: false, description: 'Lancer tous les test')
        choice(name: 'tag', choices: ['@e2e', '@smoke','@valide'], description: 'Chosissez des tag')
        booleanParam(name: 'lancer_tag', defaultValue: false, description: 'Lancer les test avec tag')
   
    }

    stages {
        stage('installe dependance'){
            steps{
                sh 'npm install'
            }
        }
        stage('lancer le test') {
                steps {
                    script {
                        if(params.lancer){
                            if(params.lancer_tag){
                                sh"npx playwright test --grep" + ${params.tag} "--project="+${params.navigateur}
                    } else {
                        sh"npx playwright test --project=" +${params.navigateur}
                    }
                    } else {
                        if (params.lancer_tag){
                            sh"npx playwright test --grep" + ${params.tag}
                    } else {
                    sh'npx playwright test'
                    }
                }
            }
        }
    }
}
}
