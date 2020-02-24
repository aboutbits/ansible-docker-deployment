Ansible Docker Deployment Role
==============================

Deployment of a Docker project.

## Role Variables

- `docker_deployment_project_name`: The name of the project (no whitespaces allowed)
- `docker_deployment_release_name`: The name of the release
- `docker_deployment_release_files`: A list of files that should be copied to the release folder (with local and remote path)
- `docker_deployment_shared_files`: A list of files that should be copied to the shared folder if they don't already exist (with local and remote path)
- `docker_deployment_aws_region`: The AWS region, where the ECR images are stored

## Example Playbook

    - hosts: all
      roles:
        - role: ansible-docker-deployment
          vars:
            docker_deployment_project_name: project-name
            docker_deployment_release_name: 1
            docker_deployment_release_files:
              - local: docker-compose.run.yml
                remote: docker-compose.yml
              - local: .env
                remote: .env
            docker_deployment_shared_files: []
            docker_deployment_aws_region: eu-west-1
