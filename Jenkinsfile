pipeline
{
 agent any
  triggers{
        pollSCM '* * * * *'
    }	
		
 stages{

    stage('Run CI?'){
        steps{
                scmSkip(deleteBuild: true, skipPattern:'.*\\[ci skip\\].*')
                sh 'echo "HI"'
            }
        }
    
    stage('Master'){
        steps{
                
                sh 'eche "JI"'
            }
        }
    }
}