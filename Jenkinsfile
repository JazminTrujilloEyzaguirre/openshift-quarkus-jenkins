pipeline {
    agent any
    stages {
        stage('Build') {
            steps {
                // Get some code from a GitHub repository
                bat script: 'git init C:\\ProgramData\\Jenkins\\.jenkins\\workspace\\ci-cd-openshift-quarkus\n' +
                             'git fetch --tags --force --progress -- https://github.com/JazminTrujilloEyzaguirre/openshift-quarkus-jenkins.git +refs/heads/*:refs/remotes/origin/*\n' +
                             'git config remote.origin.url https://github.com/JazminTrujilloEyzaguirre/openshift-quarkus-jenkins.git\n' +
                             'git config --add remote.origin.fetch +refs/heads/*:refs/remotes/origin/*\n' +
                             'git rev-parse "refs/remotes/origin/main^{commit}"\n' +
                             'git rev-parse "origin/main^{commit}"\n'

                // Run Maven on a Unix agent.
                bat script: 'mvn clean package -DskipTests=true'
            }
        }
        stage('Test') {
            steps {
                // Run Maven on a Unix agent.
                bat script: 'mvn test'
            }
        }
    }
}
