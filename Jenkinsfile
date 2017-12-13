#!/usr/bin/env groovy

node {

    properties([
            parameters([
                    string(name: 'NODE_LABEL', defaultValue: 'master'),
                    booleanParam(name: 'RUN_STAGE_1', defaultValue: true, description: 'Run Stage 1: Build an artifact'),
                    booleanParam(name: 'RUN_STAGE_2', defaultValue: true, description: 'Run Stage 2: Create an AMI'),
                    booleanParam(name: 'RUN_STAGE_3', defaultValue: true, description: 'Run Stage 3: Deploy a CFN stack')
            ])
    ])
    println "Hello...from Jeninsfile"
    println "NODE_LABEL : ${params.NODE_LABEL}"
    println "RUN_STAGE_1 : ${params.RUN_STAGE_1}"
    println "RUN_STAGE_2 : ${params.RUN_STAGE_2}"
    println "RUN_STAGE_3 : ${params.RUN_STAGE_3}"

}
