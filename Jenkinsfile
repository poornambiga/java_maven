pipeline {
    agent any
    parameters {
        choice(name: 'VERSION', choices: ['1.1.0', '1.2.0', '1.3.0'], description: '')
        booleanParam(name: 'executeTests', defaultValue: true, description: '')
    }
    stages{
        
        stage("build") {
            steps {
                script {
                    echo "build"
                }
            }
        }
        stage("test") {
            when {
                expression {
                    params.executeTests
                }
            }
            steps {
                script {
                    echo "test"
                }
            }
        }
        stage("deploy") {
            steps {
                script {
                    env.ENV = input message: "Select the environment to deploy to", ok: "Done", parameters: [choice(name: 'ONE', choices: ['dev', 'staging', 'prod'], description: '')]

                    echo "deploy"
                    echo "Deploying to ${ENV}"
                }
            }
        }
    }
}
