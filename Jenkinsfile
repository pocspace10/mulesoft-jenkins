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
        environment{
            GITHUB = credentials('POCSPACETEN')
            JFROG = credentials('JFROG')
        }
        when {
            branch 'master'
        }
        steps{ 
                sh 'git checkout master'
                sh 'git pull origin master'
                sh 'git config --global user.name pocspace10'
                sh 'git config --global user.email pocspace10@gmail.com'
                sh 'mvn -s settings.xml -B release:prepare -Darguments="-DskipTests" -DGITHUB_ACCESS_TOKEN=$GITHUB_PSW -DJFROG_PASSWORD=$JFROG_PSW'
                sh 'mvn -s settings.xml -B release:perform -Darguments="-DskipTest" -DGITHUB_ACCESS_TOKEN=$GITHUB_PSW -DJFROG_PASSWORD=$JFROG_PSW'
                sh 'cd target/checkout'
                sh 'cat pom.xml'
                sh '''
                        echo '$(find . -name '*.jar' | head -1)'
                   '''
            }
        }
    }
}