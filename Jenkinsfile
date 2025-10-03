def COLOR_MAP =[
        'SUCCESS': 'good',
        'FAILURE': 'danger',
]
pipeline{
        agent any
        stages{
                stage('Build'){
                        steps{
                                sh 'echo "Build Completed."'
                        }
                }
        }
        post{
                always{
                        echo "Slack Notifications."
                        slackSend channel: '#all-jenkins',
                                color: COLOR_MAP[currentBuild.currentResult],
                                message: "*${currentBuild.currentResult}:* Job ${env.JOB_NAME} build ${env.BUILD_NUMBER} Triggered auto"
                }
        }
}
