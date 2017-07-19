# ELK stack as docker-composer for dev-env purpose


To start environment & run it in background execute: 
----------------------------------------------------

	docker-compose up -d
   
   
To check status and available ports execute:
--------------------------------------------

	docker-compose ps
 
 
Output:
. code_block: bash

		[pkozik@epos02 elk_demo]$ docker-compose ps
			 Name                    Command               State                       Ports
		---------------------------------------------------------------------------------------------------------
		pkozik_elastic    /docker-entrypoint.sh elas ...   Up      0.0.0.0:9200->9200/tcp, 9300/tcp
		pkozik_kibana     /docker-entrypoint.sh kibana     Up      0.0.0.0:5601->5601/tcp
		pkozik_logstash   /docker-entrypoint.sh logs ...   Up      0.0.0.0:4560->4560/tcp, 0.0.0.0:4580->4580/tcp


		
To check the logs: 
------------------

 
	docker-compose logs [elastic|logstash|kibana]

	
Kibana GUI 
-----------------

Access on the IP addres of the docker host with 5601 ports


To stop environment execute:
----------------------------
    
	docker-compose stop
   
   

How to send logs to logstash?
-----------------------------

Logstash has 2 ports opened for incomming logs:
* 4560 - for raw, plain-text TCP input
* 4580 - for HTTP, plain-text input

To send TCP:
	
	echo '<log message>' | nc localhost 4560


To send HTTP:

	curl -XPOST localhost:4580 -d'<log message>'


How to check my logs in elasticsearch
-------------------------------------

Get name of the index:

	curl -XGET localhost:9200/_cat/indices
	
Once you know the name of your index:

	curl localhost:9200/<index name>-*/_search?pretty
	
