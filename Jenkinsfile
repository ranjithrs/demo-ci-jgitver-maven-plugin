#!groovy

node() {
    stage('Checkout')
    checkout scm

    stage('Build')

    def mvnHome = tool 'M3'
    env.JAVA_HOME = tool 'JDK 1.8'

    if (isUnix()) {
        sh "${mvnHome}/bin/mvn -version"
        sh "${mvnHome}/bin/mvn -Prun-its clean verify"
    } else {
        bat "${mvnHome}\\bin\\mvn -version"
        bat "${mvnHome}\\bin\\mvn -Prun-its clean verify"
    }

    stage('Local installation')
    if (isUnix()) {
        sh "${mvnHome}/bin/mvn -DskipTests install"
    } else {
        bat "${mvnHome}\\bin\\mvn -DskipTests install"
    }
}
