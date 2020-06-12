node {

    stage('Clone Repository') {
        checkout scm
                }

    stage('Get Scan Results') {
        withCredentials([usernamePassword(credentialsId: 'twistlock_creds', passwordVariable: 'TL_PASS', usernameVariable: 'TL_USER')]) {
            sh 'curl -i -k -s -u $TL_USER:$TL_PASS -H "Content-Type: application/json" -X GET "https://$TL_CONSOLE/api/v1/images?name=${env.image_name}&layers=true" > images_scan_results.json'
        }
    }
}
