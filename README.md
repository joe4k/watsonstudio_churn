# watsonstudio_churn
This repository was forked from the original repository [DSX-Local-Telco-Churn](https://github.com/elenalowery/DSX-Local-Telco-Churn) and updated to work with Watson Studio on IBM Cloud.

Effectively, this notebook shows how you can create a predictive machine learning model using Spark ML in Watson Studio to predict the likelihood of a customer to churn based on historical data. Furtheremore, the notebook also shows how you can deploy the predictive model using Machine Learning service to a REST API that you can use in your application for real-time churn prediction.

## Required Services
This notebook requires the following three services which you can create on [IBM Cloud](https://ibm.com/cloud).
1. [Watson Studio](https://console.bluemix.net/catalog/services/watson-studio): Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts for end-to-end data exploration, analysis and insights using the most popular open source machine learning packages and frameworks.
2. [Cloud Object Storage](https://console.bluemix.net/catalog/services/cloud-object-storage): IBM Cloud Object Storage is a highly scalable cloud storage service, designed for high durability, resiliency and security.
3. [Apache Spark](https://console.bluemix.net/catalog/services/apache-spark): Apache Spark service on IBM Cloud is a hosted offering for Apache Spark which is an open source cluster computing framework optimized for extremely fast and large scale data processing, which you can access via the newly integrated notebook interface IBM Analytics for Apache Spark. You can connect to your existing data sources or take advantage of the on-demand big data optimization of Object Storage. 
4. [Machine Learning](https://console.bluemix.net/catalog/services/machine-learning): IBM Watson Machine Learning is a full-service IBM Cloud offering that makes it easy for developers and data scientists to work together to integrate predictive capabilities with their applications. Machine Learning services provides you with the advantage of efficient machine learning models management (continuous learning system) and deployment (online, batch, streaming). 

To create these services, you need to have an [IBM Cloud](https://ibm.com/cloud) account. You can [sign up](https://console.bluemix.net/registration/) for an IBM Cloud account if you don't already have one.

### Cloud Object Storage
- Log into your [IBM Cloud](https://ibm.com/cloud) account
- Navigate to **Catalog**.
- Click on **Storage** category in the left navigation column.
- Select **Object Storage** service, provide a name for the service (or use default name), choose the Lite plan, and click Create.

### Apache Spark
- Log into your [IBM Cloud](https://ibm.com/cloud) account
- Navigate to **Catalog**.
- Click on **Data & Analytics** category in the left navigation column.
- Select **Apache Spark** service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.

### Machine Learning
- Log into your [IBM Cloud](https://ibm.com/cloud) account
- Navigate to **Catalog**.
- Click on **Watson** category in the left navigation column.
- Select **Machine Learning** service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
- Once the service is created, its info page is loaded. Click on **Service Credentials** in the left navigation column. If no credentials are created, click on **New Credentials** to create a new set of credentials.
```
{
  "url": "https://ibm-watson-ml.mybluemix.net",
  "access_key": "*********",
  "username": "**********",
  "password": "**********",
  "instance_id": "************"
}
```
- Copy the credentials as we'll need them in the notebook to save the trained ML model.

### Watson Studio
- Log into your [IBM Cloud](https://ibm.com/cloud) account
- Navigate to **Catalog**.
- Click on **Watson** category in the left navigation column.
- Select **Watson Studio** service, provide a name for the service (or use default name), choose the Lite plan (only use Lite plan for evaluation), and click Create.
- Once the service is created, its info page is loaded. Click on  **Get Started** to launch Watson studio.

To execute this notebook:
1. In Watson Studio, create a new Project and select the Complete option.
2. Provide a project name and under Define Storage, select the cloud object storage instance to associate with your project. If you haven't created any cloud object storage instances, click **Add** to associate a Cloud Object Storage instance with your project. If you already have a Cloud Object Storage created, you can select it. If not, you can step through the screens to create a Cloud Object Storage service and associate it with your project.
3. Associate an Apache Spark service with your project:
   - In your project, navigate to the **Settings** tab and scroll down to the **Associated Services** section.
   - Click on the *Add Service* drop down and select Spark ==> this will load the Apache Spark service page on IBM Cloud.
   - If you have already created the Apache Spark service, select the *Existing* tab and select the Apache Spark service you want to associate with your project. If not, then selec the *New* tab to create a new Apache Spark service. Select the Lite plan and click **Create**.
   - Provide a name for the service (or use the auto-generated name) and select the Lite plan and the Space (any of your IBM Cloud spaces; you may only have one). Click **Confirm**.
   ==> This would associate an Apache Spark service with your project which we need later on since we'll use SparkML machine learning code in the notebook.
4. In your project, under the **Assets** tab, click on New Notebook.
5. Provide a name for the notebook, and click on the **From URL** tab and provide the URL link for the notebook:
https://github.com/joe4k/watsonstudio_churn/blob/master/notebooks/telco-churn-sparkML.ipynb
6. For the runtime, select the Apache Spark service instance you had associated with your project.
7. Click **Create Notebook**
This would load the notebook in Watson Studio
8. Execute the steps of the notebook.
