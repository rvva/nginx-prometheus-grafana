# Nginx, Prometheus and Grafana with docker-compose!

It's a simple example, template of usage stack Nginx, Prometheus (Node Exporter, Nginx Exporter, Cadvisor) and Grafana.

### I. What will you get here?
1. Nginx with https - selfsigned certificate.
2. Prometheus for storing metrics. 
3. Prometheus-node-exporter for monitoring your operating system.
4. Prometheus-nginx-exporter for monitoring your nginx.
5. Cadvisor for monitoring your containers.
6. Grafana to visualize data. 

### II. How to run it?
1. Clone repository to your working directory:
<pre>https://github.com/rvva/nginx-prometheus-grafana/</pre>
2. Create Prometheus and Grafana data directory:
<pre>mkdir -p nginx-prometheus-grafana/{prometheus,grafana}/data</pre>
3. Change files permissions:
<pre>
sudo chown 472:0 -Rc nginx-prometheus-grafana/grafana/data
sudo chown -Rc 65534:65534 nginx-prometheus-grafana/prometheus/data
</pre>
4. Configure .env file 

Before runing containers check .env file and verify that <i>DOCKER_BRIDGE_IP_ADDRESS</i> is the same as yours.
You can check that using command:
<pre>docker network inspect bridge | grep Gateway</pre>
Modify <i>GF_SECURITY_ADMIN</i> parameters to set your personal Grafana credentials. 

5. Run it!
<pre>
docker-compose up -d
</pre>

### III. Post installation steps
1. Login into Grafana localhost:3000 and add Data Source -> Prometheus. 
2. As url address use DOCKER_BRIDGE_IP_ADDRESS:9090. 
3. Add dashboards. I recommend you:
* for nginx: https://grafana.com/grafana/dashboards/12708
* for cadvisor: https://grafana.com/grafana/dashboards/13946
* for node: https://grafana.com/grafana/dashboards/1860
