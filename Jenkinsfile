        pipeline {
    agent {
        dockerfile {
            args '-v $HOME/.m2:/root/.m2'
        }
    }
    
    environment{

        CC = 'clang'
        id=BUILD_ID

    }
    stages {
	    
        stage('build') {
            steps {
               git url: 'https://github.com/vekatkriish/javaenv.git'
                sh "mvn clean org.jacoco:jacoco-maven-plugin:prepare-agent package sonar:sonar \
    -Dsonar.host.url=https://sonarcloud.io \
    -Dsonar.organization=vekatkriish-github \
    -Dsonar.login=2a09b4d0059d6fa5ccb060e560199c80deb7b68a"
                sh "cd target && ls -al"  
                sh "echo $CC"
                sh "echo id"
            }
        }
    }
}
