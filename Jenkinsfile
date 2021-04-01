node(label: 'on-demand') {
    stage('Set up Parameters'){
        echo 'Setting up parameters...'
        script{
            properties([
                choice(
                    choices: ['Win7', 'Win10'],
                    name: 'OS'
                ),
                choice(
                    choices: ['API', 'UI'],
                    name: 'Type'
                )
            ])
        }
    }
    stage('Build') {
        echo 'Building...'
    }
    stage('Test') {
        echo 'Testing...'
    }
    stage('Deploy') {
        echo 'Deploying...'
    }
}