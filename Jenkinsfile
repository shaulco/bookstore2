#!groovy

def doCheckmarxScan(Map params) {
    def projectName = params.projectName;
    def teamName = params.teamName;
    step([$class: 'CxScanBuilder', comment: '', credentialsId: '', excludeFolders: '', excludeOpenSourceFolders: '', exclusionsSetting: 'job', failBuildOnNewResults: true, failBuildOnNewSeverity: "HIGH", filterPattern: '''!**/_cvs/**/*, !**/.svn/**/*,   !**/.hg/**/*,   !**/.git/**/*,  !**/.bzr/**/*, !**/bin/**/*,
          !**/obj/**/*,  !**/backup/**/*, !**/.idea/**/*, !**/*.DS_Store, !**/*.ipr,     !**/*.iws, !**/*.pdf, !target/**/*,
          !**/*.bak,     !**/*.tmp,       !**/*.aac,      !**/*.aif,      !**/*.iff,     !**/*.m3u, !**/*.mid, !**/*.mp3,
          !**/*.mpa,     !**/*.ra,        !**/*.wav,      !**/*.wma,      !**/*.3g2,     !**/*.3gp, !**/*.asf, !**/*.asx,
          !**/*.avi,     !**/*.flv,       !**/*.mov,      !**/*.mp4,      !**/*.mpg,     !**/*.rm,  !**/*.swf, !**/*.vob,
          !**/*.wmv,     !**/*.bmp,       !**/*.gif,      !**/*.jpg,      !**/*.png,     !**/*.psd, !**/*.tif, !**/*.swf,
          !**/*.jar,     !**/*.zip,       !**/*.rar,      !**/*.exe,      !**/*.dll,     !**/*.pdb, !**/*.7z,  !**/*.gz,
          !**/*.tar.gz,  !**/*.tar,       !**/*.gz,       !**/*.ahtm,     !**/*.ahtml,   !**/*.fhtml, !**/*.hdm,
          !**/*.hdml,    !**/*.hsql,      !**/*.ht,       !**/*.hta,      !**/*.htc,     !**/*.htd, !**/*.war, !**/*.ear,
          !**/*.htmls,   !**/*.ihtml,     !**/*.mht,      !**/*.mhtm,     !**/*.mhtml,   !**/*.ssi, !**/*.stm,
          !**/*.stml,    !**/*.ttml,      !**/*.txn,      !**/*.xhtm,     !**/*.xhtml,   !**/*.class, !**/*.iml, !Checkmarx/Reports/*.*''', fullScanCycle: 10, generatePdfReport: true, teamPath: "CxServer", highThreshold: null, includeOpenSourceFolders: '', incremental: false, mediumThreshold: null, osaArchiveIncludePatterns: '*.zip, *.war, *.ear, *.tgz', osaInstallBeforeScan: false, password: '', preset: '42', projectName: "$projectName", serverUrl: 'http://10.32.2.230', sourceEncoding: '1', username: '', vulnerabilityThresholdEnabled: true, vulnerabilityThresholdResult: "FAILURE", waitForResultsEnabled: true]);

}

pipeline {
    agent any
    stages {

        stage('Checkout') {
            steps {
                script{                           
                    dir("test") {
                        git(
                            url:'https://github.com/shaulco/Bookstore.git',
                            branch:"master"
                        )
                        doCheckmarxScan(projectName: "$JOB_NAME", teamName: "CxServer")
                    }
                }
            }
        }
    }

}
