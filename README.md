# parametersInJenkins
# Demo file for Jenkins Parameters

# defining variables in Environment block

pipeline {
    agent any

    environment{
        VAR_ENVIRONMENT    = 'dev'
        VAR_CONFIG_PATH    = '/home/ec2-user/environment.config'

        PASSWORD_SECRET    = credentials('databasepassword')

        VAR_PROPERTY_FILE_PATH = '/home/ec2-user/myproject/propertyfile-${DEPLOYMENT_CHOICE}.config'
    }

    parameters {
        choice(
            name: 'DEPLOYMENT_CHOICE',
            choices: ['dev','sit','uat','prod'],
            description: 'deployment environment choices  - choose in which env you want to deploy'
        )

        choice(
            name: 'CREATION_OR_DELETION_FOLDER_CHOICE',
            choices: ['create-folder','delete-folder'],
            description: 'Action Choice etc etc to learn different stage execution based on user choice '
        )

        string(
            name: 'NAME_OF_DEVELOPER'
            defaultValue: 'MAN-VER'
            description: 'this is an example to understand the behaviour of string parametre in jenkins'
        )
    }

    stages {
        
        stage('Set Environment Varibales which may be required in the next steps') {
            steps {
                echo 'Hello   - This is a block where we can set environment variables based on different decisions  - like what values user have choosen '
                script{

                    if ( "${DEPLOYMENT_CHOICE}" == 'dev'){
                        env.DEPLOYMENT_FOLDER = "DEV_FOLDER"
                    } else if ( "${DEPLOYMENT_CHOICE}" == 'sit'){
                        env.DEPLOYMENT_FOLDER = "SIT_FOLDER"
                    } else if ( "${DEPLOYMENT_CHOICE}" == 'uat'){
                        env.DEPLOYMENT_FOLDER = "UAT_FOLDER"
                    } else if ( "${DEPLOYMENT_CHOICE}" == 'prod'){
                        env.DEPLOYMENT_FOLDER = "PROD_FOLDER"
                    }

                }
            }
        }


        stage('Download Artefact from Artifactory') {
            steps {
                echo 'This block can be used to download package from artifactory, or to download other repo code , or any other pre requisistes etc'
                script{

                    //sh "wget https://artefactory/url/path/of/package"
                    //sh "unzip mypackage.zip"
                    //etc etc etc

                }
            }
        }


        stage('Capture Secret variables from Jenkins Secrets ') {
            steps {
                echo 'Capture Secret variables from Jenkins Secrets'
                script{

                    //sh "wget https://artefactory/url/path/of/package"


                }
            }
        }


        stage('CREATE a Folder') {
            when {
                expression {
                    params.CREATION_OR_DELETION_FOLDER_CHOICE == 'create-folder'
                }
            }
            steps {
                echo 'This step ONLY AND ONLY execute when user selects to CREATE a folder'
                script{
                    // sdo whatever u want to do here
                }
            }
        }

        stage('DELETE a Folder') {
            when {
                expression {
                    params.CREATION_OR_DELETION_FOLDER_CHOICE == 'delete-folder'
                }
            }

            steps {
                echo 'This step ONLY AND ONLY execute when user select delete folder step'
                script{

                    //whatever u want to do here


                }
            }
        }





    }
}
