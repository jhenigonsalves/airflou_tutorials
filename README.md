# Airflow for Beginners
The notes here came from the oficial documentation of Apache Airflow 

Airflow is compatible with the folowing python versions:
- Python 3.7, 
- Python 3.8, 
- Python 3.9, 
- Python 3.10.

And installing it using *pip* is the only supported way of installation. But it can be done using *poetry* or *pip-tools* using some *workaround* way.
## Quick Start
We can change the default home folder with, just changing the path:
``` python
    export AIRFLOW_HOME=~/airflow
```
It's necessary to specify the versions of airflow itself, python and the constraint url, wich can be done respectively by:
``` Python
    AIRFLOW_VERSION=2.5.3
    PYTHON_VERSION="$(python --version | cut -d " " -f 2 | cut -d "." -f 1-2)"
    # The line above will get the python version installed (or used in the venv)
    CONSTRAINT_URL="https://raw.githubusercontent.com/apache/airflow/constraints-${AIRFLOW_VERSION}/constraints-${PYTHON_VERSION}.txt"
    # For example: https://raw.githubusercontent.com/apache/airflow/constraints-2.5.3/constraints-3.7.txt
```
With the constraints defined we can finally install airflow:

``` Python
    pip install "apache-airflow==${AIRFLOW_VERSION}" --constraint "${CONSTRAINT_URL}"
```
To initialise the database, make a user and start all componentes
``` python
    airflow standalone
```
To start just open in your browser ```localhost:8080```, it will re uest an user and password. 
Both of them will be generated with the standalone command and it will **appear among the init message at the terminal** (just look carefully, it's kinda of hidden among all the text).

