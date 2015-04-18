#Git Auto Deployment 
Git duto deployment using POST deploy hooks that are offered by GitHub and BitBucket.

***
## Install
* create a directory for deployment control site
```bash
mkdir /var/www/deploy
cd /var/www/deploy
```
* clone this repo
```bash
git clone https://github.com/golfer007/git-deploy.git .
```
* setup apache/nginx/other web-server site (ex. deploy.some.site) to /var/www/deploy 

## Setup
* rename deploy-config.example.php to deploy-config.php
* fill deploy config with your repos
```php
$repos = array(
    'examplerepo' => array(
		'master' => array(
            'branch' => 'master',
            'path' => '/path/to/local/master/code/'
        ),
		'develop' => array(
            'branch' => 'develop',
            'path' => '/path/to/local/develop/code/'
        )
	),
    
    'examplerepo2' => array(
		'master' => array(
            'branch' => 'master',
            'path' => '/path/to/local/master/code/'
        ),
		'develop' => array(
            'branch' => 'develop',
            'path' => '/path/to/local/develop/code/'
        )
	)
);
```
* setup GitHub/Bitbucket POST hooks
 * GitHub (https://help.github.com/articles/post-receive-hooks) to http://deploy.some.site/github.php
 * Bitbucket (https://confluence.atlassian.com/display/BITBUCKET/POST+Service+Management) to http://deploy.some.site/bitbucket.php

### Private repos
* create local ssh key
```bash
ssh-keygen -t rsa -f ~/.ssh/id_rsa -C 'Bitbucket deploy'
```
* add public key as Deploy Key to your repo 

More: https://confluence.atlassian.com/pages/viewpage.action?pageId=271943168

## Usage
* commit and push 

# Thank You
http://lkwdwrd.com/git-auto-deployment/
