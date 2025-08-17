pipeline {
    agent any

    stages {
        stage('Checkout') {
            steps {
                git branch: 'main', 
                    url: 'https://github.com/hinakausarmulla78609-pixel/KatalonTestDemo.git'
            }
        }

        stage('Execute Katalon Tests') {
            steps {
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
}
