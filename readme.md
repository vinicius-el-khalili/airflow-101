https://campus.datacamp.com/courses/introduction-to-apache-airflow-in-python/

### 1. Introduction to Apache Airflow
workflow
- a set of steps to accomplish a data engineering task
- basically, it's a set of steps to do anything: copy, filter, write, run pipelines, ML models, *whatever, really*...

airflow

- airflow is a platform to program the **creation, scheduling & monitoring** of workflows
- can implement programs from any language, but workflows are written in **Python**
- implements workflows as **Directed Acyclic Graphs** (DAGs)
- can be accesed via code, command-line or via web interface / REST API

other workflow tools

- spotify/luigi
- SSIS
- bash scripting

Directed Acyclic Graph

- yes, it is indeed a **Directed Acyclic Graph**
- represents the set of tasks to make up the workflow
- consists of the **tasks** and the **dependencies** between tasks
- DAGs are create with vaious details such as start date, name, owner etc

DAG code example

```python
etl_dag = DAG(
    dag_id:'etl_pipeline',
    default_args={'start_date':'2025-01-01'}
)
```

running a workflow in airflow

- runnning a simple airflow task
```bash
airflow tasks test <dag_id> <task_id> [execution_date]
```

### 2. Airflow DAGs

Directed Acyclic Graph
- **Directed**: there is an inherent flow representing dependencies between components
- **Acyclic**: does not loop/cycle/repeat
- **Graph**: the actual set of taks and relationships/dependencies between them
- it's a broader concept in mathematics but the terms *DAG* and *workflow* are used seemlessly in the context of airflow, *just because*

within Airflow, DAGs:

- are written in Python (but can use components written in other languages)
- are made up of **components** (tipically tasks) to be executed, such as **operators**, **sensors**, **schedulers**, **workers**, **triggers** etc

define a DAG
- example DAG
```python
from airflow import DAG
from datetime import datetime
default_arguments = {
    'owner': 'jdoe',
    'email': 'jdoe@datacamp.com',
    'start_date' :datetime(2020,1,20)
}
```