pipeline {
    agent {
        label 'linux'
    }
    stages {
        stage('Git') {
            steps{
                git branch: 'main', credentialsId: 'fd6bde76-2dad-46bb-9a94-afb0f2858141', url: 'git@github.com:Ingvar78/vector-role.git'
            }
        }
        stage('Test'){
            steps{
                echo 'Test steps'
            }
        }
        stage('Molecule install') {
            steps{
                sh 'pip3 install --user "molecule==3.4.0" "molecule_docker" "ansible-lint<6.0.0" flake8'
                sh 'docker --version && ansible --version && ansible-lint --version && molecule --version'
                sh 'pwd'
            }
        }
        stage('Molecule test'){
            steps{
                sh 'molecule test'
                cleanWs()
            }
        }
    }
}
