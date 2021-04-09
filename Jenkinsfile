node(label: 'on-demand') {
    //  set up job parameters
    properties([
        parameters([
            choice(
                choices: ['Win7', 'Win10'],
                name: 'OS'
            ),
            choice(
                choices: ['API', 'UI'],
                name: 'TYPE'
            )
        ])
    ])
    stage('Confirm Git Installed') {
        echo 'Confirming Git is installed...'
        if (bat(
            script: "git --version",
            returnStatus: true
        ) == 0) {
            echo 'Git is installed'
        }
        else {
            echo 'Git is not installed'
            //  TODO: Fail job?
        }
    }
    stage('Confirm Maven Not Installed') {
        echo 'Confirming Maven is not installed...'
        if (bat(
            script: "mvn -v",
            returnStatus: true
        ) != 0) {
            echo 'Maven is not installed'
        }
        else {
            echo 'Maven is installed'
            //  TODO: Fail job?
        }
    }
    stage('Install Maven') {
        echo 'Using Maven plugin...'
        //  requires https://plugins.jenkins.io/pipeline-maven/
        withMaven(
            maven: "maven-3.6.3"
        ) {
            bat('mvn -v')
        }
    }
    stage('Create JSON File') {
        echo 'Creating JSON file...'
        //  requires https://plugins.jenkins.io/pipeline-utility-steps/
        writeJSON file: env.BUILD_TAG + '-params.json', json: ['OS': params.OS, 'Type': params.TYPE]
    }
    stage('Archive JSON File') {
        echo 'Archiving JSON file...'
        archiveArtifacts artifacts: env.BUILD_TAG + '-params.json'
    }
}