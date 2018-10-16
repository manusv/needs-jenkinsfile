pipeline {
  agent {
    docker {
      image 'node:6'
    }

  }
  stages {
    stage('Server') {
      parallel {
        stage('Server') {
          agent {
            docker {
              image 'maven:3.5.4-jdk-10-slim'
            }

          }
          steps {
            sh '''echo "building the server code"
mvn -version
mkdir -p target
touch "target/server.war"'''
            stash(name: 'server', includes: '**/*.war')
          }
        }
        stage('client') {
          steps {
            sh '''echo "building the client code.."
npm install --save react
mkdir -p dist
cat > dist/index.html <<EOF
Hello!
EOF
touch "dist/client.js"'''
          }
        }
      }
    }
  }
}