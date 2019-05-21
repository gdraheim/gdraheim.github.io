# Jenkins Parallel Checkout

Using multipe modules in one build can take some time for 
the initial clone, especially when the modules are spread
over multiple git repositories.

However having multiple git repositories can even be an
advantage when using parallel checkouts. It is not quite
obvious however to do that in the Jenkinsfile - so here
is an example.

* https://issues.jenkins-ci.org/browse/JENKINS-39768
* Julien Pivotto added a comment - 2016-11-16 11:48

    stage('test'){
        node {
            checkouts = [:]
            for (i=0; i<30; i++) {
                def x = i
                checkouts["foo${x}"] = {
                    checkout([$class: 'GitSCM', branches: [[name: '*/master']],
                    doGenerateSubmoduleConfigurations: false, extensions:
                    [[$class: 'RelativeTargetDirectory', relativeTargetDir: "foo${x}"],
                    [$class: 'ScmName', name: "foo${x}"]],
                    submoduleCfg: [], userRemoteConfigs: [[url: "/tmp/foo${x}"]]])
               }
            }
            parallel checkouts
        }
    }
