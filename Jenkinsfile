#!/usr/bin/env groovy

node {

    properties([
            [pipelineTriggers([[$class: 'GitHubPushTrigger']])],
            parameters([
                    string(name: 'NODE_LABEL', defaultValue: 'master', description: 'Input node for run'),
                    booleanParam(name: 'RUN_STAGE_1', defaultValue: true, description: 'Run Stage 1: Build an artifact'),
                    booleanParam(name: 'RUN_STAGE_2', defaultValue: true, description: 'Run Stage 2: Create an AMI'),
                    booleanParam(name: 'RUN_STAGE_3', defaultValue: true, description: 'Run Stage 3: Deploy a CFN stack')
            ])
    ])
    println "Hello...from Jeninsfile"
    println "Hello...from Jeninsfile"

    stage("Test1") {
        println "NODE_LABEL : ${params.NODE_LABEL}"
    }

    stage("Test2") {
        println "RUN_STAGE_1 : ${params.RUN_STAGE_1}"
        println "RUN_STAGE_2 : ${params.RUN_STAGE_2}"
        println "RUN_STAGE_3 : ${params.RUN_STAGE_3}"
    }


}
