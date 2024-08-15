
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
       stage ('deployment to prod manually'){
                                   steps{sshagent(['deploy-to-tomcat']){
                 input 'Do you approve deployement?' 
                 sh 'scp -o StrictHostkeyChecking=no webapp/target/webapp.warwithMavene37c161d/maven-spy-20240815-173311-7789580188422561609050.log ec2-user@172.31.3.160:/usr/share/tomcat/webapps'
                 }
                }}

    }
}

