# ELK stack as docker-composer for dev-env purpose


To start environment & run it in background execute: 
----------------------------------------------------

. code_block: bash

   docker-compose up -d
   
   
To check status and available ports execute:
--------------------------------------------

. code_block: bash
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

. code_block: bash
 
    docker-compose logs [elastic|logstash|kibana]

	
Kibana GUI 
-----------------

Access on the IP addres of the docker host with 5601 ports


To stop environment execute:
----------------------------
    
. code_block: bash

   docker-compose stop
   
   
