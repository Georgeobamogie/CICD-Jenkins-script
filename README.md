# CICD-Jenkins-script

This is a jenkinsfile used to build test and upload artifacts into nexus. It is also used to deploy into dev and prod environments with a manual step included for production (continuous delivery)

Replace <NEXUS_URL> and <REPOSITORY_ID> with actual values. The input step provides a manual approval step before deploying to the production cluster.
