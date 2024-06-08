
Phase 1 (Extract the service) --> 
	Phase 2 (Migrate the Reads extracted service) --> 
		Phase 3--> (Migrate the writes extracted service) -->
			Phase 4 --> (Direct requests to extracted service & disable the feature from the monolith)  
### Comparison and Evaluation Method

Extract the service in phases -
- Phase 1: creating a separate service, start to read data from the main DB, compare the fetched data for accuracy.
- Phase 2: Start to write with monolith and with extracted service, write into the shadow database using the extracted service
- Phase 3: Compare the data accuracy with the comparison framework
- Phase 4: On validation and checks write to the main data with the extracted service.

![[Pasted image 20240609030351.png]]

