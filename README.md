# Airflow for Beginners
The notes here came from the oficial documentation of Apache Airflow 

Airflow is compatible with the folowing python versions:
- Python 3.7, 
- Python 3.8, 
- Python 3.9, 
- Python 3.10.

And installing it using *pip* is the only supported way of installation. But it can be done using *poetry* or *pip-tools* using some *workaround* way.
## Quick Start
- We can change the default home folder with, just changing the path:
``` python
    export AIRFLOW_HOME=~/airflow
```

``` Python
    # Install Airflow using the constraints file
    AIRFLOW_VERSION=2.5.3
    PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
    # For example: 3.7
    CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
    # For example: https://raw.githubusercontent.com/apache/airflow/constraints-2.5.3/constraints-3.7.txt
    pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"

    # The Standalone command will initialise the database, make a user,
    # and start all components for you.
    airflow standalone

    # Visit localhost:8080 in the browser and use the admin account details
    # shown on the terminal to login.
    # Enable the example_bash_operator DAG in the home page
```
