# watsonstudio_churn
This repository was forked from the original repository [DSX-Local-Telco-Churn](https://github.com/elenalowery/DSX-Local-Telco-Churn)
and updated to work with Watson Studio on IBM Cloud.

Effectively, this notebook shows how you can create a predictive machine learning model using Spark ML in Watson Studio to predict
likelihood of a customer to churn based on historical data.

To execute this notebook:
1. Create Watson Studio service instance on IBM Cloud.
2. Open your Watson Studio instance.
3. Create a new Project and select the Complete option.
4. Provide a project name and under Define Storage, click **Add** to associate a Cloud Object Storage instance with your project.
5. In your project, under the **Assets** tab, click on New Notebook.
6. Provide a name for the notebook, and click on the ** From URL ** tab and provide the URL link for the notebook:
https://github.com/joe4k/watsonstudio_churn/blob/master/notebooks/telco-churn-sparkML.ipynb
7. Click **Create Notebook**
This would load the notebook in Watson Studio
8. Execute the steps of the notebook.
