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
                        name: 'Type'
                    )
                ])
            ])
        }
    }
    stage('Create JSON File') {
        echo 'Creating JSON file...'
        script{
            def amap = ['OS': params.OS, 'Type': params.Type]
            writeJSON file: 'params.json', json: amap
        }
    }
    stage('Archiving JSON File') {
        echo 'Archiving JSON file...'
        archiveArtifacts artifacts: 'params.json'
    }
}