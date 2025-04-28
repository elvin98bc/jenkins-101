pipeline {
    agent { 
        node {
            label 'docker-agent-python'
        }
    }
    triggers {
        pollSCM '* * * * *'
    }
    stages {
        stage('Build') {
            steps {
                echo "Building.."
                sh '''
                # Check python and pip versions
                python3 --version
                pip3 --version
                
                # Create a virtual environment
                python3 -m venv venv
                
                # Activate the virtual environment
                . venv/bin/activate
                
                # Install dependencies inside the virtual environment
                pip install -r myapp/requirements.txt
                '''
            }
        }
        stage('Test') {
            steps {
                echo "Testing.."
                sh '''
                # Activate virtual environment
                . venv/bin/activate
                
                # Run tests
                python3 myapp/hello.py
                python3 myapp/hello.py --name=Elvin
                '''
            }
        }
        stage('Deliver') {
            steps {
                echo 'Deliver....'
                sh '''
                echo "doing delivery stuff.."
                '''
            }
        }
    }
}