def git_branch = ""
pipeline {
        agent {label 'helloworld_slave'} 
        parameters{
                choice (name: 'git_branch', choices:["master","devolop","INT"])
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
                                println "this is for test"
                          } 
                }
                stage ("deploy") {
                        steps {
                                script {
                                if ( "${git_branch}" == "master" )
                                {
                                        println "this is master"
                                }
                                 else if ( "${git_branch}" == "develop" )
                                {
                                        println "this is develop"
                                }
                                        else if ( "${git_branch}" == "INT" )
                                {
                                        println "this is INT"
                                }
                                 else
                                {
                                        println "this is wrong statement"
                                }
                        }
                        }
                }
        }
}

