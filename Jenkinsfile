pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/hinakausarmulla78609-pixel/KatalonTestDemo.git'
            }
        }

        stage('Dev Environment') {
            steps {
                echo 'Setting up Dev environment...'
                
            }
        }

        stage('Test Environment') {
            steps {
                echo 'Setting up Test environment...'
                
            }
        }

        stage('UAT Environment') {
            steps {
                echo 'Setting up UAT environment...'
                
            }
        }

        stage('Execute Katalon Tests') {
            steps {
               
                catchError(buildResult: 'FAILURE', stageResult: 'FAILURE') {
                    bat """
                    "C:\\Users\\hinak\\Katalon_Studio_Engine_Windows_64-10.3.0\\katalonc.exe" ^
                    -projectPath="C:\\Users\\hinak\\Katalon Studio\\KatalonTestDemo\\KatalonTestDemo.prj" ^
                    -retry=0 ^
                    -testSuitePath="Test Suites/LoginDetails" ^
                    -browserType="Chrome" ^
                    -executionProfile="default" ^
                    -apiKey="a2170353-0537-45d0-839e-1da229297b60" ^
                    --config -proxy.auth.option=NO_PROXY -proxy.system.option=NO_PROXY ^
                    -proxy.system.applyToDesiredCapabilities=true -webui.autoUpdateDrivers=true
                    """
                }
            }
        }

        stage('Reporting') {
            steps {
                echo 'Generating Katalon Test Report...'
                publishHTML(target: [
                    allowMissing: false,
                    alwaysLinkToLastBuild: true,
                    keepAll: true,
                    reportDir: 'Reports',   
                    reportFiles: '**/LoginDetails/**/*.html',
                    reportName: 'Katalon Test Report'
                ])
            }
        }
    }
}
