pipeline {
    agent any

    environment {
        TOMCAT_WEBAPPS = '/var/lib/tomcat9/webapps' // Set this to the actual path of the Tomcat webapps directory
        TOMCAT_SERVER = 'http://54.80.115.152:8091' // Set the Tomcat server IP address and port
        TOMCAT_USER = 'tomcat' // Set this to your Tomcat server's username
        TOMCAT_PASSWORD = 'password' // Set this to your Tomcat server's password
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
                    sh "cp index1.html ${tomcatWebappsDir}"

                    // Deploy the copied file to the Tomcat server
                    sh "curl -u ${env.TOMCAT_USER}:${env.TOMCAT_PASSWORD} -T ${tomcatWebappsDir}index1.html ${env.TOMCAT_SERVER}/manager/text/deploy?path=/&update=true"
                }
            }
        }
    }
}
