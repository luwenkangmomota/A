trigger:
- main

pool:
  vmImage: ubuntu-latest

steps:
- task: NodeTool@0
  inputs:
    versionSpec: '14.x'
  displayName: 'Install Node.js'

- script: |
    npm install -g apifox-cli
    apifox run http://192.168.10.208:5699/api/v1/projects/345396/api-test/ci-config/345129/detail?token=xoh1rWd8r4z6rG_mG0O-so -r html,cli
  displayName: 'Install Apifox CLI and Run Tests'
