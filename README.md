# Pear-Radio Ansible

Pear-Radio Ansible provides the essential playbooks and inventory templates to deploy a Pear-Radio streamer effortlessly using [Ansible](https://github.com/ansible/ansible).

## Prerequisites

Before using this playbook, ensure the following prerequisites are met:

- The host running Ansible must have the [docker-py](https://docker-py.readthedocs.io/en/stable/) module installed. You can install it using the following command:

  ```bash
  pip install 'docker-py>=1.7.0'
  ```

- The target node should have [Docker](https://docs.docker.com/engine/install/) installed.

## Getting Started

Follow these steps to deploy the Pear-Radio streamer:

1. Fill out and uncomment the inventory template (`inventory.ini`). Replace the placeholder values with appropriate configurations:

   ```ini
   [streamers]
   127.0.0.1

   [streamers:vars]
   stream_seed=test_seed
   stream_username=test_username
   stream_description=test_description
   stream_tags=#test_tag
   volume_folder=/root/tracks
   ```

2. Verify the inventory to ensure it's correctly populated:

   ```bash
   ansible-inventory -i inventory.ini --list
   ```

3. Setup the controlled node using the provided playbook:

   ```bash
   ansible-playbook -i inventory.ini setup.yml
   ```

4. Run the playbook to set up the streamer container:

   ```bash
   ansible-playbook -i inventory.ini streamer-setup.yml
   ```

5. For more information on the container's functionality, refer to the [pear-radio-streamer-docker repository](https://github.com/rafapaezbas/pear-radio-streamer-docker).
