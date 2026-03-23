pipeline {
  agent any

  stages {

    stage('Install') {
      steps {
        sh """
          python3 -m venv venv
          . venv/bin/activate
          pip install --upgrade pip
          pip install -r requirements.txt
        """
      }
    }

    stage('Test') {
      steps {
        sh '''
          set -e
          . venv/bin/activate
          pytest || EC=$?
          if [ "${EC:-0}" -eq 5 ]; then
            echo "pytest found no tests (exit code 5). Treating as success."
            exit 0
          fi
          exit ${EC:-0}
        '''
      }
    }

    stage('Run app.py') {
      steps {
        sh """
          . venv/bin/activate
          python app.py
        """
      }
    }

    stage('Run pythonfile.py') {
      steps {
        sh """
          . venv/bin/activate
          python pythonfile.py
        """
      }
    }
    stage('Run python123.py') {
      steps {
        sh """
          . venv/bin/activate
          python python123.py
        """
      }
    }
    

  } // end stages
} // end pipeline
