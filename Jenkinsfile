pipeline {

    agent any

    

    tools{

        

        maven "M3"

         }

         

    stages {

        stage ('Git Checkout') {

            steps {

                git 'https://github.com/suraj/java-maven-junit-helloworld.git'

            }

        }

        stage ('Maven Build')  {

            steps {

        bat "mvn -Dmaven.test.failure.ignore=true clean package"

            }

        }

                stage ('Upload Artifacts') {

            steps {

                script {

                    def server = Artifactory.server 'artifactory'

                    def uploadSpec = """{

                        "files": [{

                       "pattern": "*",

                       "target": "DALHC/"

                    }]

                 }"""

                 

                 server.upload(uploadSpec)

                    }

                }

           }

           

           stage ('Postbuild')   {

                steps { 

                                   archiveArtifacts 'target/*.jar'

                      buildJob (‘Job2’)

                }

           }

        }

        

    

}
