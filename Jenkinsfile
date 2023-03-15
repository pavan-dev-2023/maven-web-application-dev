node{
    def mavenHome = tool name: "maven3.8.5"
    stage('checkout'){
        git credentialsId: '0cdfc56e-ec1f-412b-a186-a182ffd5dc9b', url: 'https://github.com/pavan-dev-2023/maven-web-application-dev.git'
    }
    stage('build'){
        sh "$mavenHome/bin/mvn clean package"
    }
    stage('sonarReport'){
        sh "$mavenHome/bin/mvn sonar:sonar"
    }
    stage('tomcatDeploy'){
        sshagent(['b1b1f552-7bb5-48b1-9eeb-c07e9570d4eb']) {
             sh "scp -o StrictHostKeyChecking=no target/maven-web-application.war ec2-user@54.91.110.84:/opt/apache-tomcat-10.1.7/webapps/"
                // some block
}
    }
}
