# airflow_comic_test
Follow 'leemengtw/airflow-tutorials' to have basic understanding of Airflow

## Step-by-step Note

### Clone project and Setting Enviroment:

```
## Clone project:
$ git clone https://github.com/leemengtaiwan/airflow-tutorials.git
$ cd airflow-tutorials

## Env:
$ conda create -n airflow-tutorials python=3.6 -y
...
## Package Plan ##

  environment location: /home/pyfu/anaconda3/envs/airflow-tutorials

  added / updated specs:
    - python=3.6


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    certifi-2021.5.30          |   py36h06a4308_0         141 KB
    pip-21.2.2                 |   py36h06a4308_0         2.1 MB
    python-3.6.13              |       h12debd9_1        32.5 MB
    setuptools-58.0.4          |   py36h06a4308_0         979 KB
    wheel-0.37.1               |     pyhd3eb1b0_0          31 KB
    ------------------------------------------------------------
                                           Total:        35.7 MB
...
# To activate this environment, use
#
#     $ conda activate airflow-tutorials
#
# To deactivate an active environment, use
#
#     $ conda deactivate
```

Install Crypto and Slack

* [Integrating Slack Alerts in Airflow](https://medium.com/datareply/integrating-slack-alerts-in-airflow-c9dcd155105)
* [Apache Installation Doc](https://airflow.apache.org/docs/apache-airflow/1.10.8/installation.html)
* [How to quickly get and use a Slack API token](https://medium.com/datareply/integrating-slack-alerts-in-airflow-c9dcd155105)
* [Fundamental Concepts](https://airflow.apache.org/docs/apache-airflow/stable/tutorial/fundamentals.html)

```
$ conda activate airflow-tutorials
$ pip install "apache-airflow[crypto, slack]"
(...install for a long time)

$ export AIRFLOW_HOME="$(pwd)"
$ echo $AIRFLOW_HOME 
/home/pyfu/my_projects/airflow_comic_test/airflow-tutorials


$ airflow db init
/home/pyfu/anaconda3/envs/airflow-tutorials/lib/python3.6/site-packages/airflow/models/crypto.py:21 CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.6.
DB: sqlite:////home/pyfu/my_projects/airflow_comic_test/airflow-tutorials/airflow.db
...
INFO  [airflow.models.dag] Sync 2 DAGs
INFO  [airflow.models.dag] Setting next_dagrun for example_subdag_operator.section-1 to None
INFO  [airflow.models.dag] Setting next_dagrun for example_subdag_operator.section-2 to None
Initialization done



## Run AirFlow web server
$ airflow webserver -p 8080
/home/pyfu/anaconda3/envs/airflow-tutorials/lib/python3.6/site-packages/sqlalchemy_utils/types/encrypted/encrypted_type.py:16 CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.6.
  ____________       _____________
 ____    |__( )_________  __/__  /________      __
____  /| |_  /__  ___/_  /_ __  /_  __ \_ | /| / /
___  ___ |  / _  /   _  __/ _  / / /_/ /_ |/ |/ /
 _/_/  |_/_/  /_/    /_/    /_/  \____/____/|__/
[2023-07-14 15:29:13,264] {dagbag.py:500} INFO - Filling up the DagBag from /dev/null
[2023-07-14 15:29:13,299] {manager.py:779} WARNING - No user yet created, use flask fab command to do it.
[2023-07-14 15:29:13,383] {manager.py:496} INFO - Created Permission View: menu access on List Users
[2023-07-14 15:29:13,391] {manager.py:558} INFO - Added Permission menu access on List Users to role Admin
...
Running the Gunicorn Server with:
Workers: 4 sync
Host: 0.0.0.0:8080
Timeout: 120
Logfiles: - -
Access Logformat: 
=================================================================            
[2023-07-14 15:29:15 +0800] [22455] [INFO] Starting gunicorn 20.1.0
[2023-07-14 15:29:15 +0800] [22455] [INFO] Listening at: http://0.0.0.0:8080 (22455)
[2023-07-14 15:29:15 +0800] [22455] [INFO] Using worker: sync
[2023-07-14 15:29:15 +0800] [22459] [INFO] Booting worker with pid: 22459
[2023-07-14 15:29:15 +0800] [22460] [INFO] Booting worker with pid: 22460
[2023-07-14 15:29:15 +0800] [22461] [INFO] Booting worker with pid: 22461
[2023-07-14 15:29:15 +0800] [22462] [INFO] Booting worker with pid: 22462
...
```

Open [http://localhost:8080/](http://localhost:8080/)

Because we need to have a user to login into the system, we carate user:

User1: admin / admin

```
$ airflow users create \
>       --username admin \
>       --firstname POYING \
>       --lastname FU \
>       --role Admin \
>       --email spashleyfu@gmail.com
/home/pyfu/anaconda3/envs/airflow-tutorials/lib/python3.6/site-packages/sqlalchemy_utils/types/encrypted/encrypted_type.py:16 CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.6.
[2023-07-14 16:28:41,568] {manager.py:779} WARNING - No user yet created, use flask fab command to do it.
[2023-07-14 16:28:41,797] {manager.py:512} WARNING - Refused to delete permission view, assoc with role exists DAG Runs.can_create Admin
Password:
Repeat for confirmation:
[2023-07-14 16:28:54,816] {manager.py:214} INFO - Added user admin
User "admin" created with role "Admin"

## List users:
$ airflow users list         
/home/pyfu/anaconda3/envs/airflow-tutorials/lib/python3.6/site-packages/sqlalchemy_utils/types/encrypted/encrypted_type.py:16 CryptographyDeprecationWarning: Python 3.6 is no longer supported by the Python core team. Therefore, support for it is deprecated in cryptography. The next release of cryptography will remove support for Python 3.6.
id | username | email                | first_name | last_name | roles
===+==========+======================+============+===========+======
1  | admin    | spashleyfu@gmail.com | POYING     | FU        | Admin

```

Edit `**/home/pyfu/my_projects/airflow_comic_test/airflow-tutorials/webserver_config.py**`


### Create GitHub App API

1. Go to https://api.slack.com/apps
2. Settings:
  * https://api.slack.com/apps/A05GB0KHYER
  * You have to add at least one redirect URL before you can distribute your app. 

### Write Airflow DAG:








