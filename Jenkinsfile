node(label: 'on-demand') {
    stage('Set up Parameters'){
        echo 'Setting up parameters...'
        script{
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
        }
    }
    stage('Create JSON File') {
        echo 'Creating JSON file...'
        writeJSON file: env.BUILD_TAG + '-params.json', json: ['OS': params.OS, 'Type': params.TYPE]
    }
    stage('Archiving JSON File') {
        echo 'Archiving JSON file...'
        archiveArtifacts artifacts: env.BUILD_TAG + '-params.json'
    }
}