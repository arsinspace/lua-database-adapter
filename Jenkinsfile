pipeline {
    stages {
        stage('clone repo') {
            steps{
                checkout([$class                           : 'GitSCM', branches: [[name: '*/develop']],
                          doGenerateSubmoduleConfigurations: false,
                          extensions                       : [],
                          submoduleCfg                     : [],
                          userRemoteConfigs                : [[credentialsId: 'e737692f-f974-4afa-879f-1b25210e46c4',
                                                               url          :  'https://github.com/arsinspace/lua-database-adapter']]
                          ])
            }
        }
        stage('build gradle') {
            steps{
                catchError(buildResult: 'SUCCESS', stageResult: 'FAILURE') {
                  withGradle {
                    bat """.\\gradlew build"""
                  }
                }
            }
        }
    }
}
