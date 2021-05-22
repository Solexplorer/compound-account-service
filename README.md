# compound-account-service
- use eventscanner.py to collect all transfer events involving COMP
    - starts off from the last block scanned
    - continually update using a service file
- we place this collection of accounts in MongoDB
    - one collection contains all transfer events
    - another collection contains details of accounts in a real time fashion, formatted like COMP's API
- using these COMP_accounts, we then derive the requested information from these accounts
- We create a service that queries for new COMP transfers, this can be set in the service file
    - a timer mechanism is used to dictate blockchain scanning refresh intervals
- we update the correspond collections (accounts, and account-info) as we go
    - as this is a service it will run in the background
    - using COMP's existing API as bootstrapping mechanism, we can save a lot on resources, make sure not to abuse it.

![alt text](https://github.com/dirtybits/compound-account-service/blob/main/compound_service_architecture.png)
