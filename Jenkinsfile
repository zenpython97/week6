// week5 example uses Jenkin's "scripted" syntax, as opposed to its "declarative" syntax
// see: https://www.jenkins.io/doc/book/pipeline/syntax/#scripted-pipeline
// Defines a Kubernetes pod template that can be used to create nodes.
podTemplate(containers: [
          containerTemplate(
          name: 'gradle', image: 'gradle:6.3-jdk14', command: 'sleep', args: '30d'
          ),
     ]) {
          node(POD_LABEL) {
               stage('Run pipeline against a gradle project') {
                    // "container" Selects a container of the agent pod so that all shell steps are
                    // executed in that container.
                    container('gradle') {
                         stage('Build a gradle project') {
                              // from the git plugin
                              // https://www.jenkins.io/doc/pipeline/steps/git/
                              git 'https://github.com/zenpython97/Continuous-Delivery-with-Docker-and-Jenkins-Second-Edition.git'
                              sh '''
                              echo webhook launched ..........
                              echo this is testing branch
                              cd Chapter08/sample1
                              chmod +x gradlew
                              ./gradlew test
                              '''
                         }
                    }
               }
          }
     }
