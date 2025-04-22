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

Admins will need to copy over the promotion flow dev-stg-prod-flow.yaml under workshop-templates/resources/configurations/promotion-flows into the same path in the codefresh-isc.  

1. Create branch
``` console
git checkout -b add-default-promotion-flow
```
2. Copy default promotion flow
``` console
cp workshop-templates/resources/configurations/promotion-flows/dev-stg-prod-flow.yaml codefresh-isc/resources/configurations/promotion-flows/dev-stg-prod-flow.yaml
```
3. Add file, commmit and push
``` console
git add resources/configurations/promotion-flows/dev-stg-prod-flow.yaml
git commit -m "Add default promotion flow"
git push --set-upstream origin add-default-promotion-flow
```
4. Open pull request against main branch and merge

All products share this default promotion flow.

Users will need to come back to this repository to pick up their product workshop-templates/resources/configurations/products.

# Codefresh Workshop Setup Instructions for Users

1. Set the following variables before running commands
``` console
export ABBR=<Your Short Abbreviation, no longer than 4 characters>
```
2. Clone your codefresh-isc repository.
``` console
git clone ...
```
3. Copy all product files form cf-workshop into codefresh-isc at same relative path.
```
cp -r workshop-templates/resources/configurations/products ../codefresh-isc/resources/configurations/products
```
4. Create branch based on your abbreviation. 
``` console
git checkout -b $ABBR
```
5. Replace abbr in filename.
``` console
mv abbr-infrastructure.yaml $ABBR-infrastructure.yaml
mv abbr-result.yaml $ABBR-result.yaml
mv abbr-vote.yaml $ABBR-vote.yaml
mv abbr-worker.yaml $ABBR-worker.yaml
```
6. Replace abbr in files.
``` console
cd ../codefresh-isc/resources/configurations/products && find . -type f -name "*.yaml" -exec sed -i .bak -e "s|abbr|$ABBR|g" {} +
```
7. Add files, commmit and push
``` console
git add .
git commit -m "Add files for $ABBR"
git push --set-upstream origin $ABBR
```
8. Open pull request against main branch and merge
