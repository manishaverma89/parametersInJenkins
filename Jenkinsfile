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
             env = params.Environments
             sh 'mkdir -p $env'
             sh 'cd $env'
             sh 'mkdir -p test2'
             
             if ( params.Environments == 'DEV'){
             
             echo "Hello  from DEV branch"
             sh 'pwd'
             sh 'ls -lart'
             sh 'mkdir -p DEV'
             sh 'cd DEV'
             sh 'mkdir -p DEV/dir1'
             sh 'pwd'
             sh 'ls -lart'
             sh 'ls DEV'
            
        }
             else{
                  echo "Hello this is from ${params.Environments} branch "
             } 
     }
    }
    }
    }
}
