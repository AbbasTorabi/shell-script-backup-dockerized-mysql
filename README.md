# shell scipt to get backup dockerized mysql
This script connect to your mysql and get databases list, then exclude mysql default databases and get backup the rest of databases.

## Requirements
- docker [install docker](https://docs.docker.com/get-docker/)
- docker compose [install docker compose](https://docs.docker.com/compose/install/)
- Make sure that you have a Python entry in your PATH! Windows requires an environmental variable to be set at `My Computer ‣ Properties ‣ Advanced ‣ Environment Variables`. There's a few Stack Overflow questions about this.

## Config Mysql
### Config your mysql step by step:
- Docker compose:
```
-s => Save the results to your local file.
-g => Save the results to your local file and also push to your GitHub repo.
-c => Receive the results in a CSV format instead of JSON
```
- Using multiple flags is fine, but avoid using both `-s` & `-g` as this will duplicate your results.
- There are some script variables used to control the time format, wait time between tests and the results filename. Find them here:
```
currentTime
waitTime
resultsFile
```
- The wait time is in seconds.
