pipeline
{
 agent any
  triggers{
        pollSCM '* * * * *'
    }	
		
 stages{

    stage('Run CI?'){
        steps{
                scmSkip(deleteBuild: false, skipPattern:'.*\\[ci skip\\].*')
            }
        }
    
    stage('Master'){
        steps{ 

            when {
                branch 'master'
            }
                sh 'git checkout master'
                sh 'git pull origin master'
                sh 'git config --global user.name pocspace10'
                sh 'git config --global user.email pocspace10@gmail.com'
                sh 'mvn -s settings.xml -B release:prepare -Darguments="-DskipTests"'
                sh 'mvn -s settings.xml -B release:perform -Darguments="-DskipTest"'
            }
        }
    }
}