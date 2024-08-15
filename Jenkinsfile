
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
    }
}

