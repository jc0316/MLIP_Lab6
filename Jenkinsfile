pipeline {
    agent any

    stages {
        stage('Build') {
            steps {
                sh '''#!/bin/bash
                echo 'In C or Java, we can compile our program in this step'
                echo 'In Python, we can build our package here or skip this step'
                '''
            }
        }
        stage('Test') {
            steps {
                sh '''#!/bin/bash
                echo 'Test Step: Setting up virtual environment and running tests'

                # Define virtual environment path
                VENV_PATH="venv"

                # Remove old virtual environment if it exists
                if [ -d "$VENV_PATH" ]; then
                    echo "Removing existing virtual environment..."
                    rm -rf $VENV_PATH
                fi

                # Create a new virtual environment
                echo "Creating a new virtual environment..."
                python3 -m venv $VENV_PATH

                # Activate the virtual environment
                source $VENV_PATH/bin/activate

                # Upgrade pip and install dependencies
                echo "Installing dependencies from requirements.txt..."
                pip install --upgrade pip
                pip install -r requirements.txt

                # Run pytest (ensure the test directory is correct)
                echo "Running tests with pytest..."
                pytest tests/  # Modify path if needed

                # Deactivate virtual environment
                deactivate

                echo 'Tests completed successfully'
                '''
            }
        }
        stage('Deploy') {
            steps {
                echo 'In this step, we deploy our porject'
                echo 'Depending on the context, we may publish the project artifact or upload pickle files'
            }
        }
    }
}
