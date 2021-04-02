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