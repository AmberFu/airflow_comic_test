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
```

### Create GitHub App API

1. Go to https://api.slack.com/apps
2. Settings:
  * https://api.slack.com/apps/A05GB0KHYER
  * You have to add at least one redirect URL before you can distribute your app. 

### Write Airflow DAG:








