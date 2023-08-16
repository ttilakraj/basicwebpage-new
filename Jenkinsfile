pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/var/lib/tomcat9/webapps' // Set this to the actual path of the Tomcat webapps directory
    }

    stages {
        stage('Checkout') {
            steps {
                // Checkout the code from the Git repository
                checkout scm
            }
        }
        stage('Copy HTML to Tomcat') {
           steps {
                script {
                    def tomcatWebappsDir = "/var/lib/tomcat9/webapps/ROOT/"
                    sh "cp index.html ${tomcatWebappsDir}"
                }
            }
        }
        stage('Access Main Branch HTML') {
            steps {
                script {
                    def mainBranchHtml = httpRequest(url: 'http://3.234.86.185:8090/main-branch/index.html', ignoreSslErrors: true)
                    echo mainBranchHtml.content
                }
            }
        }
    }
}
