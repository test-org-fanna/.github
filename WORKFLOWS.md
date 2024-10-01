# Workflows
explanation

### Tips to keep the maintainer happy
- Do noy create your own custom workflows but request/create one on organizational level
- Keep the tags clean; if a Docker build did not succeed, remove the tag manually

# The mother of all workflows
Caller workflows

# Workflows in steps

## Workflow : Unit Test
### A] Django
### B] Vitest

- [ ] Robot framework for integration tests

## Workflow : Integration Test
### A] Cypress
- [ ] Robot for integration tests?

## Workflow : docker-build-and-push
#### Use them
1. Input Dockerfile name(s)
2. Input Dockerfile secret(s):
   1. retrieve secrets from GitHub and set them as a matrix variable [image here]()
   2. write the secrets as a multiline environment variable [here](https://docs.docker.com/build/ci/github-actions/secrets/#secret-mounts)
   3. make sure that the names are everywhere the same [image]()
3. Make sure the following secrets/variables are available in GitHub:
   1. SECRET: DOCKER_HUB_USERNAME
   2. SECRET: DOCKER_HUB_ACCESS_TOKEN

#### Steps explained
1. Checks out the repository
2. Tags the version
   - According to [Semantic Versioning](link hier) using the prefix 'V'
   - Uses [anothrNick/github-tag-action@1](link hier) to
3. Sets the docker images tag for every Dockerfile that has been inputted
3. build -> context uses [handlebars](https://handlebarsjs.com/guide/#html-escaping)
4. secrets: strategy contexts cannot contain secrets so they need to be referenced differently [read this](https://sbulav.github.io/terraform/github-actions-matrix-secrets/)



## Workflow : deployment
### A] Kubernetes deployment
### B] SSH deployment