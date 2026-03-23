pipeline {
   agent any
   stages {
       stage('Checkout') {
           steps {
               git 'https://github.com/your-repo/your-python-project.git'
           }
       }
       stage('Setup & Run') {
           steps {
               sh '''
                   python3 -m venv venv
                   source venv/bin/activate
                   pip install --upgrade pip
                   pip install -r requirements.txt
                   python script.py
               '''
           }
       }
   }
}
