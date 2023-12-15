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
             echo "Hello from DEV branch"
             sh 'pwd'
             sh 'mkdir -p dev_1'
             sh 'ls -lart'
            
        }
             else{
                  echo "Hello from ${params.Environments} branch "
             } 
     }
    }
    }
    }
}
