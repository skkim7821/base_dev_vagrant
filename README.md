# Base Dev Vagrant
node, react, redux로 개발에 쓰이는 개발 환경을 구축합니다. 


## requirements
필수적으로 꼭 필요한 프로그램. 

* vagrant
* ansible

```shell
brew install vagrant
brew install ansible
```

## Directory Layout

```
.
├── /data/
│   ├── /mongodb/               # The folder for compiled output
│   └── /redis/					# The folder for compiled output
├── /logs/                      # Documentation files for the project
│   ├── /mongodb/               # The folder for compiled output
│   └── /redis/					# The folder for compiled output
├── /workspace/              	# 3rd-party libraries and utilities
│   ├── /front/               	# The folder for compiled output
│   ├── /front/                 # The folder for compiled output
│   └── /api/					# REST API
├── /src/                       # The source code of the application
│   ├── /actions/               # Action creators that allow to trigger a dispatch to stores
│   ├── /api/                   # REST API / Relay endpoints
│   ├── /components/            # React components
│   ├── /constants/             # Constants (action types etc.)
│   ├── /content/               # Static content (plain HTML or Markdown, Jade, you name it)
│   ├── /core/                  # Core framework and utility functions
│   ├── /decorators/            # Higher-order React components
│   ├── /public/                # Static files which are copied into the /build/public folder
│   ├── /stores/                # Stores contain the application state and logic
│   ├── /client.js              # Client-side startup script
│   ├── /config.js              # Global application settings
│   ├── /routes.js              # Universal (isomorphic) application routes
│   └── /server.js              # Server-side startup script
├── /tools/                     # Build automation scripts and utilities
│   ├── /lib/                   # Library for utility snippets
│   ├── /build.js               # Builds the project from source to output (build) folder
│   ├── /bundle.js              # Bundles the web resources into package(s) through Webpack
│   ├── /clean.js               # Cleans up the output (build) folder
│   ├── /copy.js                # Copies static files to output (build) folder
│   ├── /deploy.js              # Deploys your web application
│   ├── /run.js                 # Helper function for running build automation tasks
│   ├── /runServer.js           # Launches (or restarts) Node.js server
│   ├── /start.js               # Launches the development web server with "live reload"
│   └── /webpack.config.js      # Configurations for client-side and server-side bundles
│── package.json                # The list of 3rd party libraries and utilities
└── preprocessor.js             # ES6 transpiler settings for Jest
```


## ansible 
ansible이 하는 것들. docker, docker toolbox, nvm을 만든 후에 docker로 mongodb과 redis을 만듭니다. 

* docker
* docker toolbox
* nvm
* dockerfile
	- mongodb
	- redis 

ansible role에 해당하는 것을 ansible galaxy에서 다운 받습니다. requrements.yml은 playbook.yml에 필요한 롤들을 로컬에 다운 받게 합니다. 
```shell
ansible-galaxy install -r requirements.yml
```
기존 파일에 playbook을 추가할 경우에 강제로 기존의 설치한 것을 덮어씌움  
```shell
ansible-galaxy install -r -f requirements.yml
```

## vagrant 
vagrant를 반드시 설치해야 합니다. 기본적으로 virtualbox로 정의되어 있고 


```shell
git clone https://github.com/skkim7821/base_dev_vagrant
vagrant up
```


## nodejs
nodejs는 nvm으로 관리되며 현재는 가장 최신 버전인 node 5.0.0으로 세팅되어 있습니다. 버전이 바뀌 때마다 변경 및 관리 할 수 있습니다. 

* nvm
* node 5.0.0
* npm 
	- bower
	- forever
	- pm2
	- eslint
	- webpack
	- webpack-dev-serve


## amazon s3을 쓰기 위한 riak cs
production 환경에서 amazon s3을 고려하고 있기에 개발 시에 로컬 환경에 amazon s3와 완벽히 호환되는 riak cs로 모든 테스트를 한다. 

### docker riakcs cluster
간편하게 riak cs을 클러스트로 만들어 줌. 이것도 추후에 vagrant에 추가해서 이미지 서버로 뺄 수 있음. 

* 참고 프로젝트 [docker riakcs cluster](https://github.com/hectcastro/docker-riak-cs)

### s3cmd
s3cmd로 riak cs로 테스트한다. 

* [s3cmd 공식](http://s3tools.org/s3cmd) 

## docker로 생성되는 서비스
### mongodb
```shell
mongo host_ip:host_port
```

### redis

```shell
redis-cli -h host_ip -p host_port
```
### mailserver 

# h1 

## h2

### h3

#### h4

* list item
* list item
* list item

이 플러그인은 이런 겁니다.

```shell
npm install assemble --save-dev
```

```js
grunt.loadNpmTasks('assemble');
```

