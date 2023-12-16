pipeline {
  agent any
  parameters {
    choice(
      name: 'Environments',
      choices: ['DEV', 'UAT', 'PROD'],
      description: 'Choose An Environment'
    )
  }
  stages {
    stage('Environment') {
      steps {
        script{
             echo "The environment is: ${params.Environments}"
             if ( params.Environments == 'DEV'){
             echo "Hello  from DEV branch"
             sh 'pwd'
             sh 'cd ~'
             sh 'ls -lart'
            
        }
             else{
                  echo "Hello this is from ${params.Environments} branch "
             } 
     }
    }
    }
    }
}
