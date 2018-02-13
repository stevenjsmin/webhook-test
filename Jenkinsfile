#!/usr/bin/env groovy

node("master") {

    git url: "https://github.com/stevenjsmin/webhook-test.git", branch: 'develop'

    properties([
            pipelineTriggers([[$class: 'GitHubPushTrigger']]),
            //pipelineTriggers([[$class: 'GitHubPushTrigger'], pollSCM('H/1 * * * *')]),
            parameters([
                    string(name: 'NODE_LABEL', defaultValue: 'master', description: 'Input node for run'),
                    booleanParam(name: 'RUN_STAGE_1', defaultValue: true, description: 'Run Stage 1: Build an artifact'),
                    booleanParam(name: 'RUN_STAGE_2', defaultValue: true, description: 'Run Stage 2: Create an AMI'),
                    booleanParam(name: 'RUN_STAGE_3', defaultValue: true, description: 'Run Stage 3: Deploy a CFN stack')
            ])
    ])
    println "Hello...from Jeninsfile 1"
    println "Hello...from Jeninsfile 2"

    stage("Test1") {
        println "NODE_LABEL : ${params.NODE_LABEL}"
    }

    stage("Test2") {
        println "RUN_STAGE_1 : ${params.RUN_STAGE_1}"
        println "RUN_STAGE_2 : ${params.RUN_STAGE_2}"
        println "RUN_STAGE_3 : ${params.RUN_STAGE_3}"

        try{
            println "예외처리 테스트 1"
            //throw new Exception("어디한번 보자..")
            error("오류 발생...")
            println "예외처리 테스트 2"

        }catch(Exception e) {
            // /root/.jenkins/jobs/JenkinsPipeline1/builds
            println ("Hello~~~" + e.getMessage())
            println ("WORKSPACE:" + env.WORKSPACE)
            println ("BUILD_URL:" + env.BUILD_URL)
            println ("JENKINS_HOME:" + env.JENKINS_HOME)
            println ("BUILD_FILE:" + env.JENKINS_HOME + "/jobs/" + env.JOB_NAME + "/builds/" + env.BUILD_NUMBER + "/log")

            String fileContents = new File(env.JENKINS_HOME + "/jobs/" + env.JOB_NAME + "/builds/" + env.BUILD_NUMBER + "/log").getText('UTF-8')

            //println(fileContents);

            println("##############1")
            println( "${BUILD_LOG_EXCERPT}")
            println("##############2")


            echo 'Email test'
            emailext( subject: "[JENKINS] ${env.JOB_NAME} failed",
                    attachLog: true,
                    // body: "Build failed (see ${env.BUILD_URL}: ${error})",
                    body: "Build failed : ${fileContents}",
                    to: "stevenmin@nbnco.com.au",
                    from: "noreply@crunchcode.com.au"
            )
            throw e
        }
    }




}
