ansible_php_ci
==============

ansible scripts to setup a jenkins php CI server


To complete a jenkins job, config files for the ant job and the php tools 
need to be present in the git repositoty of the project.
Example config files the jenkins job and for the php tools are available 
in this repository
 
- jenkins.xml
  ant build file that orchestrates the execution of the various tools
- jenkins/phpcs.xml
  Code sniffer config
- jenkins/phpunit.xml
  Phpunit config file 
- jenkins/phpmnd.xml
  mess detector config
- jenkins/phpdox.xml
  phpdox config

Post install
------------
- Set security for the jenkins web interface (anyone can access it now)
- There will be a php job called php-template. Rename this to suit your project
- Go to the manage job section and set the git repository and credentials
- Manage Jenkins > Configure Global Security > and select the markup formatter as RAW HTML.
- Enable the job

Known issues
------------
During provisioning you might get a 'connection refused' error in the get jenkins client task.
This is because the jenkins service is not ready yet. Running vagrant provision again
will solve the issue.

References:
- http://erichogue.ca/2011/05/php/continuous-integration-in-php/
- http://jenkins-php.org/installation.html
- https://github.com/wearebase/jenkins-ansible-php-orchestration