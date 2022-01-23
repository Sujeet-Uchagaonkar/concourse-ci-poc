# concourse-ci-cd
# Concourse pipeline is a collection of jobs. Job is collection of tasks/steps.
  Order of jobs does not matter in pipeline, but order of tasks/ steps matters.

# Setup Concourse and CI/CD pipeline steps

- Download the Docker compose file

        `wget https://concourse-ci.org/docker-compose.yml`
- Run the Docker Compose File

        `docker-compose up -d`
- Download the fy CLI tool from the localhost:8080 (and set path parameter if require)

- Give execute permission to the fly CLI

        `chmod +x fly`
- Copy the fly CLI to the /usr/bin

        `sudo cp fly /usr/bin/`
- Login to the concourse

        `fly -t tutorial login -c http://localhost:8080 -u test -p test`

- Docker (composed version) only has linux worker. You can verify this by running :
		`fly -t tutorial workers`
		
- Clone this github project

        `git clone https://github.com/Sujeet-Uchagaonkar/concourse-ci-poc.git`

        `fly -t tutorial set-pipeline -p hello-sujeet-pipeline -c concourse-ci-poc/hello-sujeet-pipeline.yml`

- Then un-pause Concourse Pipeline

        `fly -t tutorial unpause-pipeline -p hello-sujeet-pipeline`

- Now you have successfully setup the CI/CD pipeline.

- Trigger the job named 'sujeet-concourse-poc-job' in pipeline using below command:
		`fly -t tutorial trigger-job --job hello-sujeet-pipeline/sujeet-concourse-poc-job --watch`


