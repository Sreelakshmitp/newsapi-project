# ML_ECS_pipeline
A ML containerisation project which makes use of ECS to deploy a streamlit app which can query data from postgres rds in aws which is populated using a automated labmbda function by making use of a NewsAPI

![Architecture](![1 architecture](https://github.com/user-attachments/assets/9b693c9c-4180-4419-9c8b-e372253b6c13)
)

In this project

* We are making use of a NewsAPI where we get the latest news articles with help of a API_Key obtained from the news api website
  after creating a developer account

* News articles are extracted with the help of a lambda function which is triggered every 1 hr using Event bridge.

* The raw data extrated are pushed to a S3 bucket and stored in json format
  ![]![8 S3bucket](https://github.com/user-attachments/assets/e40c0e30-ef3d-4235-929a-c59b69d4c477)

* Analyzed  news aritcle are pushed to a rds postgres AWS instance along with timestamp.
  ![](![3 database](https://github.com/user-attachments/assets/deaae039-385b-4e4b-814b-cbaac82b99d4)

  ![11 pgadmin](https://github.com/user-attachments/assets/e8a29842-c560-4fcd-b763-e0bbd8aed5c2)

* Now a Dashboard is created using Streamlit to visualize the sentiment of the news in local system which is then converted to a docker image and pushed to ECR Registry in AWS.
 
![4 dockerbuild](https://github.com/user-attachments/assets/c2906c29-8202-44b6-a2b4-66f5b1ea707a)

![5 docker-image](https://github.com/user-attachments/assets/534fef6c-41d3-4543-b7da-c54ad3dd5f58)

* The uploaded image is run using a AWS Fargate cluster by create a task definition and using the publicIP and assigned port
  we can access the Streamlit Dashboard.
  
![2 docker-cluster](https://github.com/user-attachments/assets/da1f38fd-433e-4ca9-b07c-643c20b29fd5)
![10 task-overview](https://github.com/user-attachments/assets/0b77b3cd-0106-48cc-9cfd-184dbda91e5c)
![9 task-configuration](https://github.com/user-attachments/assets/b2593035-f0ef-4f32-96e4-f6faa7fe69be)
![6 dashboard](https://github.com/user-attachments/assets/53174de1-5027-4658-8837-9f06032fe776)
