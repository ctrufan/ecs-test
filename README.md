ECS-Test role 
=========
Leveraging Deployment Automation Ansible Role to Set Up and Refresh Your Web Infrastructure
https://www.entrustdatacard.com/products/categories/ssl-certificates)
https://www.entrustdatacard.com/blog/2019/august/leveraging-deployment-automation-tools

This role creates:  and publicly signed Entrust Certificate.

	- Create Private key.
	- Create Certificate Signing Request (CSR).
    - Create, reissue, and renew certificates from Entrust Certificate Services (ECS) API.
    - Requires credentials for the (Entrust Certificate Services(ECS) API.
    - In order to request a certificate, the domain and organization used in the certificate signing request must be already
      validated in the ECS system. It is I(not) the responsibility of this module to perform those steps
	  
Requirements
---------------
	- Ansible Version 2.9
	- PyYAML >= 3.11
	- cryptography >= 1.6
    - PyOpenSSL >= 0.15 

Role Variables
----------------

Available variables can be found in (vars)

Dependencies
----------------

None

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users to have:

Before running the example you will need to: 

	1- Update the contents of files to have your ECS API certificate and key information.
	2- Update the variables in vars file as appropriate for:
       - APIusername.
	   - APIpassword.
	   - Approved domains/etc.
	3- configure the {{working_path}} to where ansible role will be installed i.e  /home/user/.ansible/roles

    Example Playbook
	
	----------------
    - hosts: localhost
      become: true
      roles:
        - ecs-test
	   
	ansible-playbook playbook.yml

----------------
	  name: Generate an Entrust certificate via the Entrust ECS API
		openssl_certificate:
		path: /etc/ssl/crt/ansible.com.crt
		csr_path: /etc/ssl/csr/ansible.com.csr
		provider: entrust
		entrust_requester_name: Bob Doe
		entrust_requester_email: bdoe@ansible.com
		entrust_requester_phone: 555-555-5555
		entrust_cert_type: UC_SSL
		entrust_api_user: api_username
		entrust_api_key: api_password
		entrust_api_client_cert_path: /etc/ssl/entrust/ecs-client.crt
		entrust_api_client_cert_key_path: /etc/ssl/entrust/ecs-key.crt
		entrust_api_specification_path: /etc/ssl/entrust/api-docs/cms-api-2.1.0.yaml

License
----------------

MIT/BSD

Author Information
----------------

This role was created by Taha Hadreez (ECS testing)
Copyright (c), Entrust Datacard Corporation, 2019
