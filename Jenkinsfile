node{

stage('checkout'){
  checkout scm

}

stage('build'){
    nodejs(nodeJSInstallationName:'nodejs'){
    
    sh npm install

    }

}

stage('test step'){
nodejs(nodeJSInstallationName:'nodejs'){
    
    sh npm run test -- -- headed

    }

}







}