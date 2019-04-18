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

Then copy the proposals.json to code/app/static/data/

## Start Daemons
Run
````
docker-compose up
````
## Import proposals.json into MongoDB
Open the URL
````
http://localhost:5000/import_data
````
## HackaTUM 
* access flask shell: `docker exec -it $(docker-compose ps -q flask) bash`
* access mongo shell: `docker exec -it $(docker-compose ps -q mongo) bash -c "mongo"`
