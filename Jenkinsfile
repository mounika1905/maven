pipeline
{
    agent any
    stages
    {
        stage('cont downnload')
        {
            steps
            {
                git 'https://github.com/mounika1905/maven.git'
            }
        }
         stage('cont build')
        {
            steps
            {
                sh 'mvn package'
            }
        }
         stage('cont deploy')
        {
            steps
            {
                input 'Hi Manager Vinod, Please approve for depolyment in QA server !'
                deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.43.82:8080')], contextPath: 'testapp', war: '**/*.war'
            }
        }
          stage('cont test')
        {
            steps
            {
                git 'https://github.com/sudarshansw7/myfunctionaltesting.git'
                sh 'java -jar /var/lib/jenkins/workspace/declarativepipeline1/testing.jar'
                
            }
        }
         stage('cont delivery')
        {
            steps
            {
                input 'Hi Manager Vinod, Please approve for depolyment in Prod server !'
                deploy adapters: [tomcat9(credentialsId: '96f64ec9-9b16-49bb-83c0-839019550937', path: '', url: 'http://172.31.38.170:8080')], contextPath: 'prodapp1', war: '**/*.war'
            }
        }
    }
}
