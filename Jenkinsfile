#!groovy

/* Only keep the 10 most recent builds. */
properties([[$class: 'BuildDiscarderProperty',
                strategy: [$class: 'LogRotator', numToKeepStr: '10']]])

stage ('Build') {

  node {
    // Checkout
    checkout scm

    // install required bundles
//    sh 'bundle install'

    sh 'bundle exec rake build spec'

    archive (includes: 'pkg/*.gem')


publishHTML(target: [	allowMissing: false, 
			alwaysLinkToLastBuild: false, 
			keepAll: true, 
			reportDir: 'coverage', 
			reportFiles: 'index.html', 
			reportName: 'RCovReport', 
			reportTitles: '', 
			useWrapperFileDirectly: true])
} }
   
