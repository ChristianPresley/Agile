# Integrating Jenkins with ServiceNow using API tokens

## DevOps CI/CD Workflow

Automated deployments are enabled by following a standard DevOps to change management workflow. For example:

1. Developer/Business Analyst creates a Pull Request in GitHub

2. Code integration is started:
   - Code linting (syntax, styles)
   - Automated unit testing (code conforms to contracts)
   - Static code analysis (package vulnerability analysis, secrets/password detection)

3. Code integration passes linting and automated linting

4. Change request record is created in ServiceNow

5. Code/changes are deployed to acceptance environment
   - Automated integration tests
   - Test plans are run and validated
   - Manual user acceptance testing (as necessary)
   - Risks are documented and added to change request record
   - Product demonstrations (as necessary)

6. Change accepted/approved

7. Product Owner/Manager determines if production deployment
    - Workflow is started to tag commit with release annotation
    - Commit is tagged and all build (CI) artifacts are marked as immutable

8. Artifacts are deployed to production as defined by the commit tag

9. Application monitoring takes over and provides health signals via dashboard and alerting

## Jenkins to ServiceNow integration steps

**NOTE: There is no IBM Nexus Repository support in ServiceNow.**

- [ServiceNow DevOps Data Model (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/34cfa6f087302300f97abba826cb0b54/1.34.1)

- [ServiceNow DevOps Change Velocity (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/f1d62f041b3abc10d6f254a5624bcbf5/1.34.1)

- [ServiceNow DevOps Insights (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/f95540c2b7203300885688b8de11a9a5/1.15.0)

- [Jenkins plug-in for ServiceNow DevOps (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/9a304cc7db185810df5ff3251d9619f3/1.34.1)

- [Jira integration for SerivceNow DevOps (storage page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/f4425e08db9c1450231df3251d961922)

- [Atlassian Jira Integration for Agile Development (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/9e8488a8c703330024f6612827c2601b/2.1.1)

- [ServiceNow DevOps integrations (store page)](https://store.servicenow.com/sn_appstore_store.do#!/store/application/ca1a857cc72600108c2c02b827c260df/1.34.1)
  - GitLab
  - Jenkins
  - Microsoft Azure DevOps
  - SonarQube
  - JFrog Artifactory

- [Jenkins Integration with ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/jenkins-integration-dev-ops.html)

- [Setting up the DevOps connection with Jenkins (video)](https://youtu.be/JlDV9JAFYNg)

- [Connect ServiceNow DevOps to Jenkins](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/connect-dev-ops-jenkins.html)

- [Modeling the Jenkins scripted pipeline with DevOps (video)](https://youtu.be/RbC5mvLU5lw)

- [Model a Jenkins pipeline in ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/task/model-jenkins-pipeline-dev-ops.html)

- [Configuring the Jenkins pipeline for ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/config-jenkins-pipeline-dev-ops.html)

- [Associate pipeline steps and Jenkins freestyle jobs in ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/task/dev-ops-associate-jenkins-steps.html)

- [Configure SonarQube scans on Jenkins pipelines](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/task/config-sonarqube-jenkins-devops.html)

- [Notify change request rejection or cancellation reason to Jenkins pipeline](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/task/update-jenkins-change-reject-reason.html)

- [Notify ServiceNow DevOps change request number to Jenkins pipelines](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/devops-change-number-notify-jenkins.html)

- [Jira integration with ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/jira-integration-dev-ops.html)

- [SonarQube integration with ServiceNow DevOps](https://docs.servicenow.com/bundle/sandiego-devops/page/product/enterprise-dev-ops/concept/sonarqube-devops-integration-devops.html)