# Worldwide Labour Force Project - End to end data pipeline
My final project of the Data Engineering Zoomcamp from [DataTalksClub](https://github.com/DataTalksClub) consisted in developing an End-to-end data pipeline that fetches, transforms and analyzes worldwide labour force data.

Through this pipeline, data is extracted from the [International Labour Organization website](https://ilostat.ilo.org/data/) and undergoes a series of carefully orchestrated processes, such as uploading to the cloud, cleaning, analysis, and visualization to provide users with accurate on labor issues across the world.

![Dashboard](https://github.com/gmzgian/Worldwide-Labour-Force-Project/blob/main/Images/Internation%20labour%20organization%20logo.webp)

## Problem ❓
While the ILOSTAT website provides a wealth of valuable labor-related data, doing ad-hoc analysis with the data provided can be problematic.

Firstly, data on the ILOSTAT website is presented in a pre-defined format, which may not always match the specific research questions or analytical approaches of the user. As a result, users may need to spend a considerable amount of time and effort reformatting and cleaning the data to suit their needs, which can be time-consuming and error-prone.

Secondly, the website provides limited data exploration and visualization capabilities. Users may not be able to customize charts, tables, or graphs based on their specific analysis requirements. This could limit the user's ability to identify patterns, relationships, or trends in the data, which are crucial for making informed decisions.

## Solution 💡
The end-to-end pipeline addresses the limitations of ad-hoc analysis by providing cleaned and structured data in the cloud, enabling users to conduct efficient and effective data exploration, analysis and visualization. With its comprehensive data collection and batch data processing, this data pipeline exemplifies the power of technology to drive social and economic progress.

## Infrastructure 💻
The following tools and technologies are used:

* Cloud - [Google Cloud Platform](https://cloud.google.com/)
* Infrastructure as Code software - [Terraform](https://www.terraform.io/)
* Containerization - [Docker](https://www.docker.com/), [Docker Compose](https://docs.docker.com/compose/)
* Batch Processing - [Python](https://www.python.org/)
* Orchestration - [Prefect](https://www.prefect.io/)
* Transformation - [Tableau Prep Builder](https://www.tableau.com/products/prep)
* Data Lake - [Google Cloud Storage](https://cloud.google.com/storage)
* Data Warehouse - [BigQuery](https://cloud.google.com/bigquery)
* Data Visualization - [Tableau](https://www.tableau.com/)

Quick descriptions of the two tools not used during the Zoomcamp
* [Tableau Prep Builder](https://www.tableau.com/products/prep): Tableau Prep Builder provides a modern approach to data preparation, making it easier and faster to combine, shape, and clean data for analysis within Tableau. By providing a visual and direct path to prep your data, you can get your hands on quality data in just a few clicks.


* [Tableau](https://www.tableau.com/): Tableau delivers everything you need to access, visualize, and analyze your data. With an intuitive drag and drop interface, you can uncover the hidden insights you need to make impactful business decisions faster.

**[Link to the live, interactive dashboard](https://public.tableau.com/views/WorldwideLabourForceAnalysis/WORLDWIDELABOURFORCEANALYSIS?:language=en-US&:display_count=n&:origin=viz_share_link)**

![Dashboard](https://github.com/gmzgian/Worldwide-Labour-Force-Project/blob/main/Images/WORLDWIDE%20LABOUR%20FORCE%20ANALYSIS.png)


## Development Steps 🔧
1. Started a Google Cloud Platform [free account](https://cloud.google.com/free/docs/free-cloud-features#free-trial).
2. Created a Virtual Machine (Linux) and a GCP project and followed the advanced steps in [here](GCP_setup/gcp_overview_setup.md).
3. Made sure the follwing software is installed in the machine: Docker and Docker-Compose, Python 3 (e.g. via Anaconda), Terraform.
4. Created a workflow using Prefect as orchestrator to download data from the ILOSTAT website, transform it into a .parquet file and upload it to Google Cloud Storage (data lake). Follow [these steps](https://github.com/gmzgian/Worldwide-Labour-Force-Project/edit/main/Data_Fetch_&_Orchestration/README.md) to orchestrate, parameterize and schedule this workflow. 
5. Uploaded two tables (Working-age population by sex, age and education (thousands) & Average monthly earnings of employees by sex and economic activity) to Google Cloud Storage and copied them over to Google BigQuery (Data warehouse). Parameters are commented at the end of the code [parameterized_etl_web_to_gcs_project.py](Data_Fetch_&_Orchestration/parameterized_etl_web_to_gcs_project.py).
6. From BigQuery, I developed a Tableau Prep Builder flow [DE_zoomcamp_project_UNION_cleansing_transformation.tflx](https://github.com/gmzgian/Worldwide-Labour-Force-Project/tree/main/Tableau%20Prep%20%26%20Tableau%20Dashboard) that automatically transforms & cleans the data from each table, unions them and then joins a [Country lookup file.xlsx](https://github.com/gmzgian/Worldwide-Labour-Force-Project/tree/main/Tableau%20Prep%20%26%20Tableau%20Dashboard). Once the flow has run, it spits out a single, ready-to-analyze table into Google BigQuery again.
7. Developed a [Tableau dashboard](https://public.tableau.com/app/profile/gianmarco415data) (file: ([WORLDWIDE LABOUR FORCE ANALYSIS.twbx](https://github.com/gmzgian/Worldwide-Labour-Force-Project/tree/main/Tableau%20Prep%20%26%20Tableau%20Dashboard)) by loading the brand new table created by the Tableau Prep builder flow. In the dashboard, I analyze the gender pay gaps, education gaps from year 2012 to year 2022 by building 6 different graphs (tiles).

![Transformation_Flow](https://github.com/gmzgian/Worldwide-Labour-Force-Project/blob/main/Images/Transformation_Flow_Tableau_Prep_Builder.png)

![Transformation_Flow](https://github.com/gmzgian/Worldwide-Labour-Force-Project/blob/main/Images/Final_project_data_pipeline.png)

**Thank you for taking the time to learn more about my project** 😊
