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
                sh 'echo "HI"'
            }
        }
    
    stage('Master'){
        steps{
                
                sh 'echo "JI"'
            }
        }
    }
}