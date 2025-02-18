
# Amazon Books Data Pipeline 
-----------


## Create a virtual environment and activate it (optional)
"""

    python -m venv venv
    source venv/bin/activate

"""


# 🔗Important links and Code
-----

## Install Airflow 
-----

Follow steps in the link - https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html

## Install PGAdmin 
-----
Code to add in yaml file 


"""

    postgres:
        image: postgres:13
        environment:
          POSTGRES_USER: airflow
          POSTGRES_PASSWORD: airflow
          POSTGRES_DB: airflow
        volumes:
          - postgres-db-volume:/var/lib/postgresql/data
        healthcheck:
          test: ["CMD", "pg_isready", "-U", "airflow"]
          interval: 10s
          retries: 5
          start_period: 5s
        restart: always
        ports:
          - "5432:5432"
    
    pgadmin:

        container_name: pgadmin4_container2
        
        image: dpage/pgadmin4
        
        restart: always
        
        environment:
        
          PGADMIN_DEFAULT_EMAIL: admin@admin.com
          PGADMIN_DEFAULT_PASSWORD: root
          
        ports:
          - "5050:80"
"""

-----

# Pipeline Design


![images](https://private-user-images.githubusercontent.com/123731672/414194037-e47c7e05-265a-4725-9565-3f616932ec05.png?jwt=eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJpc3MiOiJnaXRodWIuY29tIiwiYXVkIjoicmF3LmdpdGh1YnVzZXJjb250ZW50LmNvbSIsImtleSI6ImtleTUiLCJleHAiOjE3Mzk4NzI4NDYsIm5iZiI6MTczOTg3MjU0NiwicGF0aCI6Ii8xMjM3MzE2NzIvNDE0MTk0MDM3LWU0N2M3ZTA1LTI2NWEtNDcyNS05NTY1LTNmNjE2OTMyZWMwNS5wbmc_WC1BbXotQWxnb3JpdGhtPUFXUzQtSE1BQy1TSEEyNTYmWC1BbXotQ3JlZGVudGlhbD1BS0lBVkNPRFlMU0E1M1BRSzRaQSUyRjIwMjUwMjE4JTJGdXMtZWFzdC0xJTJGczMlMkZhd3M0X3JlcXVlc3QmWC1BbXotRGF0ZT0yMDI1MDIxOFQwOTU1NDZaJlgtQW16LUV4cGlyZXM9MzAwJlgtQW16LVNpZ25hdHVyZT04Mjk1YjEzNWU0ODZkYmY2YTBjMGY3MWM4OTUyNWM5MWFjMTFmYmJkNGZiY2JiNjJmOThjZmIwZmM0NjcwYTc0JlgtQW16LVNpZ25lZEhlYWRlcnM9aG9zdCJ9.tSCOP_Nj3glr0dr3ngLba5NP135nIkLKYVcNm1lrqAI)



