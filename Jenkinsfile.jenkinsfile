#!/usr/bin/env groovy

node('master') {
         def location = "Gravity\\Gravity.sln"
 
        stage('Stage Checkout') {
                checkout([$class: 'GitSCM', 
                branches: [[name: '*/development']], 
                doGenerateSubmoduleConfigurations: false, extensions: [], submoduleCfg: [], 
                userRemoteConfigs: [[url: 'https://github.com/tsdservices/Gravity.git']]])
        }
        stage('Stage build'){
                fileExists location
                bat 'S:/nuget.exe restore Gravity\\Gravity.sln'
                bat 'S:/nuget.exe restore Gravity\\Gravity\\packages.config -PackagesDirectory Gravity\\packages'
                bat "\"C:/Program Files (x86)/Microsoft Visual Studio/2017/Professional/MSBuild/15.0/Bin/MSBuild.exe\" Gravity\\Gravity.sln"
        }
    
}