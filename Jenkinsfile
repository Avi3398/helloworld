pipeline {
        agent any 
        parameters{
                choice (name: "git_branch", choices:["master","devolop","INT"])
        }
        stages {
                stage ("clone") {
                        steps {
                                git credentialsId: 'github', url: 'https://github.com/Avi3398/helloworld.git'
                        }
                }
                stage ("maven build") {
                steps {
                        sh "mvn clean install"
                }
                }
                stage ("test") {
                        steps {
                                script {
                                try {
                                println "this is for test"
                                }
                                catch(Exception e) {
                                        println "there is a issue in test"
                                }
                         }
                          } 
                }
                stage ("deploy") {
                        steps {
                                script {
                                if ( "${git_branch}" == "master")
                                {
                                        println "this is master"
                                }
                                 else if ( "${git_branch}" == "develop")
                                {
                                        println "this is develop"
                                } else if ( "${git_branch}" == "INT")
                                {
                                        println "this is INT"
                                }
                                 else
                                {
                                        println "this is wrong"
                                }
                        }
                        }
                }
        }
}
