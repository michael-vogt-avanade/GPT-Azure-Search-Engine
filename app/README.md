<h1 align="center">
GPT Smart Search
</h1>

Accurate answers and instant citations from documents in your Azure Data Lake.

---------------------------------------------
This was edited by Mike Vogt for Mike Vogt
This uses Cog Search and OpenAI resources SHARED by Mike and Mark to 
conserve experimentation costs.
The pages/1_GPT_Smart_Search.py file contains the statements declaring which Indexes are searchable by the web page interface generated and
served up by Home.py

MIKE - follow theses steps
1) get into AML (youre already here)
2) get into Mike's Notebook (youre already here)
3) open the GPT-Azure-Search-Engine/app README.md file (this one)
4) launch a terminal from the /app subdir... copy the four (4) export
statements from this README.md file and paste into the terminal
4) conda activate envMike311    conda environment to make sure can support the web page interface, else will error
5) streamlit run Home.py   this will return a URL, BUT, if running from an Azure ML session, MUST use the predefined vanity URL in a browser to reach this web service...
6) in separate browser, browse to
https://compute-DS11v2-mcv01-8501.eastus.instances.azureml.ms/
Select from left menu GPT Smart Search
NOTE - this will search ALL the indexes specified by the 1_GPT_Smart_Search.py statements... i.e. 
index1_name = "cogsrch-index-files"
.
.
NOTE - MIKES pages file names indexes MARKS does NOT, so search results
will be different!!!!  for the Utility industry, Mike and Mark ran Notebook 1 and dumped multiple DATA_SOURCES into one 'codsrch-index-files' index... you will find mikes ASA container content w CDP files, + marks (350) Utility industry service manuals + mixed PDFs from marks ASA container content...
------------------------------------------
## 🔧 Features

- Queries Azure Cognitive Search and uses OpenAI to provide an acurate answer.
- Translate the answer in any language
- Provides a Quick Answer and a Best Answer

## 💻 To run it Locally
1. Install dependencies

```bash
pip install -r requirements.txt
```
2. Set the environmental variales needed by the app
```bash
export AZURE_SEARCH_ENDPOINT=<Enter your value>
export AZURE_SEARCH_KEY=<Enter your value>
export AZURE_OPENAI_ENDPOINT=<Enter your value>
export AZURE_OPENAI_API_KEY=<Enter your value>

export AZURE_SEARCH_ENDPOINT="https://azure-cog-search-gtekhenxlqzvu.search.windows.net"
export AZURE_SEARCH_KEY="EPpDuVjPveOV8hhzKu7e17H0AB7QIzrWGqumQK87uEAzSeB9FqUZ"
export AZURE_OPENAI_ENDPOINT="https://oai-2023-mondelez-chatgpt-01.openai.azure.com/"
export AZURE_OPENAI_API_KEY="f86736ea92444e9f836b69de0512ca55"
```
3. Run the Streamlit server🚀
```bash
cd app
streamlit run Home.py
```
4. If you are working on an Azure ML compute instance, go to:<br>
https://{Your-AMLCompute-Name}-{port}.{your-region}.instances.azureml.ms/ 
  
Example: https://myComputeInstance-8501.southcentralus.instances.azureml.ms/ 



https://compute-DS11v2-mcv01-8501.eastus.instances.azureml.ms/


 
## To Deploy in Azure Web App Service

[![Deploy To Azure](https://aka.ms/deploytoazurebutton)](https://portal.azure.com/#create/Microsoft.Template/uri/https%3A%2F%2Fraw.githubusercontent.com%2Fpablomarin%2FGPT-Azure-Search-Engine%2Fmain%2Fapp%2Fazuredeploy.json)

1. Make Sure that once the ARM template is ready to be created in the Azure portal, you change the ***Repo Url*** variable to your own repo:
"https://github.com/<YOUR_GITHUB_NAME>/GPT-Azure-Search-Engine.git"

2. Once the deployment is done, go to **Azure Portal -> Your Web App Service -> Settings -> Congiguration -> Application Settings** and set the values of the enviromental variables needed. **Don't forget to click the SAVE button on the top**.

3. Your App should be working now.

4. Everytime you commit changes to your branch it will kick in CI/CD and deploy your changes to the web app

## Troubleshoot

- If WebApp deployed succesfully but the Application didn't start
1. Go to Azure portal -> Your Webapp -> Settings -> Configuration -> General Settings
2. Make sure that StartUp Command has:  python -m streamlit run app/Home.py --server.port 8000 --server.address 0.0.0.0

- If deployment fails with error "Cannot find SourceControlToken with name Github" you can try the following
1. Wait 20 mins and Retry
2. Delete the browser cache and retry
3. Go to the deployed WebApp and Authorize azure to deploy and build code directly from Github 

![Authorize Github](../images/error-authorize-github.jpeg "Authorize Github" )

- If running locally fails with error "TypeError: unsupported operand type(s) for |: 'type' and '_GenericAlias'"
Check your list of conda environments and activate one with Python 3.10 or higher
For example, if you are running the app on an Azure ML compute instance:
```
conda env list
conda activate azureml_py310_sdkv2
```




