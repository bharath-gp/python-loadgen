# python-loadgen

Upsert some documents into a bucket using the couchbase python client.
The tool can create documents and update them based on the count parameter.
For pure creates, give passes=1. For both create and updates, give passes=(num of mutations required + 1).
For pure updates, include update_counter = (value of update in document + 1).
For deletes, include delete and num_delete parameters.
The tool can also validate the data loaded. Include validation parameter for validation.
For no validation, give validation=0
For validation at the end of the load generation, give validation=1
For validation after each pass of mutation, give validation=2
For only validation and no mutations, give validation=3 
With validation=3, pass -update_counter=value of update in a document (and --deleted and --deleted_items=docs_deleted)
The rate of mutations can be limited using rate_limit (to the best of ability)
Expiry of documents can be set using ttl parameter
Validation of expiry of documents can be done by using --validate_expired

example to run the program:
python thanosied.py -U 10.112.176.101 -b default -p password -u Administrator -B 20 -c 1000 -P 2 -v 1 -r 1000 -T 4 --workers 2
