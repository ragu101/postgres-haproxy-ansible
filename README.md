# This is repo is used to deploy helm charts for postgres, haproxy and test them together

Role Name
=========

postgres-operator - Helm deployment of patroni backed postgres cluster

deploy-haproxy - Helm deployment of haproxy 

test-haproxy - Test postgres connectivity through HAproxy by a container

Role Variables
----------------
nameSpace - namesapce in which helm deployments will be created
basepath  - Path where the github repos will be checked out
DB_PASSWORD - Provide password for postgres
DB_HOST - Provide hostname for postgres


How to Run Playbook
----------------
#Replace appropriate values for below variables

Step 1: deploy postgres & haproxy

ansible-playbook postgres.yaml -e nameSpace=default -e basepath=/Users/ragu/Documents/git_repos/ansible-roles

Step 2: Get postgres password

kubectl get secret postgres.acid-minimal-cluster.credentials.postgresql.acid.zalan.do -o 'jsonpath={.data.password}' | base64 -d

Step 3: Test HAproxy (update below variables with appropriate values)

ansible-playbook test-haproxy.yaml -e nameSpace=default -e DB_NAME=postgres -e DB_USER=postgres -e DB_PASSWORD=<POSTGRES_PASSWORD> -e DB_HOST=haproxy -e DB_PORT=5432





