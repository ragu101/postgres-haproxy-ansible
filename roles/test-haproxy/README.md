Role Name
=========

postgres-operator - Helm deployment of patroni backed postgres cluster
deploy-haproxy - Helm deployment of haproxy 
test-haproxy - Test postgres connectivity through HAproxy by a container

How to Run Playbook
----------------
#Replace appropriate values for below variables

ansible-playbook site.yaml -e DB_PASSWORD=somePassword -e DB_HOST=172.17.0.6
