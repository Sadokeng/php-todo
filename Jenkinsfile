pipeline {
    agent any

    stages {
        stage ('Initial cleanup') {
            steps {
                dir("${WORKSPACE}") {
                    deleteDir()
                }
            }
        }

        stage ('Checkout SCM') {
            steps {
                git branch: 'main', url: 'https://github.com/Sadokeng/php-todo.git'
            }
        }

        stage ('Prepare Dependencies') {
            steps {
                sh 'mv .env.sample .env'
                sh 'composser install'
                sh 'php artisan migrate'
                sh 'php artisan key:generate'
            }
        }

    }
}