# Table of Contents
1. [Introduction](#introduction)
1. [Quick Start](#quick_start)
    1. [Sub paragraph](#subparagraph1)
1. [Key Concepts](#key_concepts)
   
# Airflow for Beginners <a name = 'Introduction'></a>
The notes here came from the oficial documentation of Apache Airflow 

Airflow is compatible with the folowing python versions:
- Python 3.7, 
- Python 3.8, 
- Python 3.9, 
- Python 3.10.

And installing it using *pip* is the only supported way of installation. But it can be done using *poetry* or *pip-tools* using some *workaround* way.
# Quick Start <a name = 'quick_start'></a>
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

# Key Concepts <a name='key_concepts'></a>
Here are some key concepts (that may be useful to have easy access when necessary):
## DAG - Directed Acycic Graph<a name= 'dag'></a>
**Definition:** It's the core concept of airflow.,organized with dependencies and relationships to say how they should run.

**Example**:
![Basic DAG](/images/basic-dag.png.png "Title")
