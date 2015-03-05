[![Build Status](https://travis-ci.org/sbugert/lab-travis-codeclimate.svg?branch=master)](https://travis-ci.org/sbugert/lab-travis-codeclimate)[![Code Climate](https://codeclimate.com/github/sbugert/lab-travis-codeclimate/badges/gpa.svg)](https://codeclimate.com/github/sbugert/lab-travis-codeclimate)[![Test Coverage](https://codeclimate.com/github/sbugert/lab-travis-codeclimate/badges/coverage.svg)](https://codeclimate.com/github/sbugert/lab-travis-codeclimate)[![Dependency Status](https://david-dm.org/sbugert/lab-travis-codeclimate.svg)](https://david-dm.org/sbugert/lab-travis-codeclimate)[![devDependency Status](https://david-dm.org/sbugert/lab-travis-codeclimate/dev-status.svg)](https://david-dm.org/sbugert/lab-travis-codeclimate#info=devDependencies)

###Demo Repo for travis-ci and code climate integration of lab tests


Set up .travis.yml:  
Add desired node versions, e.g.: 

```
language: node_js
node_js:
- '0.10'
- '0.11'
- '0.12'
- iojs
```

Run `travis encrypt secretcodeclimateapikey` after `travis login` to encrypt your API-Key and add it to .travis.yml.

```
 addons:  
 	code_climate:  
 		repo_token:  
 			secure: encodedcodeclimateapikey
```
Send lconf from lab to codeclimate by piping `lab -r lcov` to **codeclimate-test-reporter** (dev-dependency). 

```
after_script:
- npm run coverage | codeclimate
```