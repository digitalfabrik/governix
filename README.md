# A visual presentantation of http://ris-muenchen.de/ data
Governix visualizes the status of proposals in the RIS Muenchen system.

# Set Up
## Crawler
To get a list of all IDs from the RIS, in crawler.py uncomment the line 
````
  ids = get_all_proposal_ids(ids_filename)
````
If the ids.txt already exists, the document IDs can be loaded from it
instead of crawling the web. The crawler then continues to collect details
about all documents in the file proposals.json.

## Start Daemons
Run
````
  docker-compose -f docker-compose.yml up
````
## Import proposals.json into MongoDB
````
  mongoimport -d hackatumdb -c proposals --jsonArray < proposals.json
````
## HackaTUM 
* access flask shell: `docker exec -it $(docker-compose ps -q flask) bash`
* access mongo shell: `docker exec -it $(docker-compose ps -q mongo) bash -c "mongo"`
