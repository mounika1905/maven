node('built-in')
{
    stage('git checkout')
    {
        git 'https://github.com/intelliqittrainings/maven.git'
    }
    stage('cont build')
    {
        sh 'mvn package'
    }
    stage('cont deployment')
    {
        deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.43.82:8080')], contextPath: 'testapp', war: '**/*.war'
    }
    stage('cont testing')
    {
        git 'https://github.com/intelliqittrainings/FunctionalTesting.git'
        sh 'java -jar /var/lib/jenkins/workspace/project/testing.jar'
    }
    stage('cont delivery')
    {
        deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.38.170:8080')], contextPath: 'prodapp', war: '**/*.war'
    }
}
