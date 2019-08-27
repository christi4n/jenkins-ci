pipeline {
  agent { label 'ci-slave-php' }
  stages {
    stage('Start') {
	  steps {
	    echo 'Build process is starting...'
	    sh 'printenv'
	  }
	}
	stage('Confirmation') {
      steps {
        input('Do you want to proceed?')
      }
    }
	stage('Git clone') {
	  steps {
	      sh 'rm CmsComposerInstallers/ -Rf'
	      sh "git clone https://github.com/TYPO3/CmsComposerInstallers.git"
	  }
	}
	stage('Composer install') {
	    steps {
	        sh 'cd ${PWD}/CmsComposerInstallers'
	        sh '/usr/local/bin/php /usr/local/bin/composer clear-cache'
	        sh '/usr/local/bin/php /usr/local/bin/composer install --no-dev --working-dir=${PWD}/CmsComposerInstallers'
	    }
	}
  }
}