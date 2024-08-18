
pipeline{
    agent any
    stages{
        stage('code checkout'){
            steps{
            git branch: 'master', url: 'https://github.com/Abhinav501-eng/java-hello-world-with-maven-15-august.git'

            }
        }
              stage('code compile'){
            steps{
              withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
               sh 'mvn compile'
               }
            }
        }
            stage('code test'){
            steps{
              withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
               sh 'mvn test'
               }
            }
        }
        stage('created Packages'){
            steps{
              withMaven(globalMavenSettingsConfig: '', jdk: 'JAVA_HOME', maven: 'MAVEN_HOME', mavenSettingsConfig: '', traceability: true) {
               sh 'mvn package'
               }
            }
        }

         stage('deploye tomcat server'){
                    steps{sshagent(credentials: ['deploy-to-tomcat']) {
                 sh 'scp -o StrictHostkeyChecking=no jb-hello-world-maven-0.2.0-shaded.jar ec2-user@3.25.191.105:/usr/share/tomcat/webapps/'
                 }
                }}


    }
}

