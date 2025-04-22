# Codefresh Workshop Setup Instructions for Account Administrator

The purpose of this workshop is to gain a base understanding of Codefresh Pipelines & GitOps Cloud.

The workshop contains a simple 5 microservice sample application.

The intended usage is to setup and configure this application per user for them to have a sandbox application they can develop against.

If you're taking the instructor lead workshop the following repositories should already be available in your GitHub Organization.

https://github.com/salesdemocf/cf-apps
https://github.com/salesdemocf/cf-configs
https://github.com/salesdemocf/cf-pipelines
https://github.com/salesdemocf/cf-result
https://github.com/salesdemocf/cf-vote
https://github.com/salesdemocf/cf-worker

If you do not have these or are the Account Administrator please reach out to your assigned SE, TAM or CSM for additional assistance.

If you are an Account Administrator.  Please copy the repositories above to your GitHub Organization.

In your Codefresh Account please configure the following integrations.

Pipeline Integrations

- [GIT](https://codefresh.io/docs/docs/integrations/git-providers/#github)
- [Image Registry](https://codefresh.io/docs/docs/integrations/docker-registries/)

GitOps Integrations

- [Image Registry](https://codefresh.io/docs/docs/gitops-integrations/container-registries/)

In your Codefresh Account install a GitOps Cloud Runtime

- [Installation Instructions](https://codefresh.io/docs/docs/gitops-quick-start/quick-start-install-runtime/)

Users will need to come back to this repository to pick up their product workshop-templates/resources/configurations/products.

1. Clone your codefresh-isc repository.
1. Copy all product files form cf-workshop into codefresh-isc at same relative path.
1. Replace abbr in filename and within file under metadata.name with your abbreviation.
1. Create a branch on codefresh-isc repository with your changes and submit PR to main branch and merge.

Admins will need to copy over the promotion flow dev-stg-prod-flow.yaml under workshop-templates/resources/configurations/promotion-flows into the same path in the codefresh-isc.  

All products share that default promotion flow.