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
             sh 'ls -lart'
             sh 'mkdir -p DEV'
             sh 'cd DEV'
             sh 'mkdir -p DEV/dir1'
             sh 'pwd'
             sh 'ls -lart'
             sh 'ls DEVi'
            
        }
             else{
                  echo "Hello this is from ${params.Environments} branch "
             } 
     }
    }
    }
    }
}
