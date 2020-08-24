# OpenStack Infrastructure Monitoring

` This Project is for setting up Monitoring stack where node-exporter is installed on the VM or node you want to monitor.`

` Prometheus, Grafana and alert-manager is running in docker container using docker-compose. `

` Installation Script for Node exporter install_node_exporter.sh `

# Clone the Repo
` git clone  `

` cd openstack-infrastructure-monitoring/ `

# Make changes to prometheus.yml, alertmanager.yml, datasource.yml accordingly .
` docker-compose up -d `

` docker ps -a `
