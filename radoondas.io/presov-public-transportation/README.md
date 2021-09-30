# Open data for public transportation in Prešov

**Note:** This is still work in progress and will be finished with the blog release. The documentation will be also updated.

Complete guide to the setup WILL BE on my blog [radoondas.io](https://radoondas.io/).

1. Clone the git repository
```
git clone https://github.com/radoondas/examples.git
```
2.
```bash
$ cd examples/radoondas.io/presov-public-transportation
```
3. Spin up ES cluster with Kibana
```bash
$ docker-compose up -d
```
4. Check if Elasticsearch and Kibana works
 ```
 http://127.0.0.1:9200
 http://127.0.0.1:5601
 ```
5. Index data - periodically
```bash
docker run --rm -it --network=host \
  -v $(pwd)/conf/logstash.conf:/usr/share/logstash/pipeline/logstash.conf \
  -v $(pwd)/conf/dpmp_template.json:/usr/share/logstash/config/dpmp_template.json \
  -v $(pwd)/conf/logstash.yml:/usr/share/logstash/config/logstash.yml \
  docker.elastic.co/logstash/logstash:7.15.0
  ```
6. Kibana - Create Indext pattern
7. Visualize in Kibana Maps (Import saved objects)
