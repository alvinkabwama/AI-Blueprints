# 🤖 Vanilla RAG with LangChain

<div align="center">

![Python](https://img.shields.io/badge/Python-3.11+-blue.svg?logo=python)
![Jupyter](https://img.shields.io/badge/Jupyter-supported-orange.svg?logo=jupyter)
![LangChain](https://img.shields.io/badge/LangChain-used-lightgreen.svg?logo=langchain)
![HuggingFace](https://img.shields.io/badge/Hugging--Face-model-yellow.svg?logo=huggingface)
![MLflow](https://img.shields.io/badge/MLflow-enabled-blue.svg?logo=mlflow)
![Streamlit UI](https://img.shields.io/badge/User%20Interface-Streamlit-ff4b4b.svg?logo=streamlit)

</div>

# 📚 Contents

- [🧠 Overview](#overview)
- [🗂 Project Structure](#project-structure)
- [⚙️ Setup](#setup)
- [🚀 Usage](#usage)
- [📞 Contact and Support](#contact-and-support)

---

## Overview

This project is an AI-powered vanilla **RAG (Retrieval-Augmented Generation)** chatbot built using **LangChain**. It leverages the **Z by HP AI Studio Local GenAI image** and the Meta Llama 3.1 model with 8B parameters to generate contextual and document-grounded answers to user queries about **Z by HP AI Studio**.

---

## Project Structure

```
├── core
│   └── chatbot_service                                                 # Core Python modules
│       ├── __init__.py
│       └── chatbot_service.py
├── data                                                                # Data assets
│   └── AIStudioDoc.pdf                                                 # AIStudio documentation
├── demo                                                                # UI-related files
│   ├── assets
│   ├── index.html
│   ├── source
│   └── streamlit-webapp
├── docs
│   ├── html_ui_for_vanilla_rag.png                                     # HTML UI Screenshot
│   ├── streamlit_ui_for_vanilla_rag.png.png                            # Streamlit UI Screenshot
│   └── successful streamlit ui result for vanilla rag.pdf              # Successful Streamlit UI Screenshot
├── notebooks
│   ├── register-model.ipynb                                             # Model registration notebook
│   └── run-workflow.ipynb                                               # Main workflow notebook
├── README.md                                                           # Project documentation
└── requirements.txt                                                    # Python dependencies
```

---

## Setup

### Step 0: Minimum Hardware Requirements

To ensure smooth execution and reliable model deployment, make sure your system meets the following minimum hardware specifications:

- RAM: 64 GB
- VRAM: 12 GB
- GPU: NVIDIA GPU

### Step 1: Create an AI Studio Project

- Create a new project in [Z by HP AI Studio](https://zdocs.datascience.hp.com/docs/aistudio/overview).

### Step 2: Set Up a Workspace

- Choose **Local GenAI** as the base image.

### Step 3: Clone the Repository

1. Clone the GitHub repository:

   ```
   git clone https://github.com/HPInc/AI-Blueprints.git
   ```

2. Ensure all files are available after workspace creation.

### Step 4: Add the Model to Workspace

- Download the **LLaMA2-7B** model from AWS S3 using the Models tab in your AI Studio project:
  - **Model Name**: `meta-llama3.1-8b-Q8`
  - **Model Source**: `AWS S3`
  - **S3 URI**: `s3://149536453923-hpaistudio-public-assets/Meta-Llama-3.1-8B-Instruct-Q8_0`
  - **Bucket Region**: `us-west-2`
- Make sure that the model is in the `datafabric` folder inside your workspace. If the model does not appear after downloading, please restart your workspace.

### Step 5: Configure Secrets and Paths

- Add your API keys to the `secrets.yaml` file located in the `configs` folder:
  - `HUGGINGFACE_API_KEY`: Required to use Hugging Face-hosted models instead of a local LLaMA model.
- Edit `config.yaml` with relevant configuration details.

---

## Usage

### Step 1: Run the Notebook

Execute the notebook inside the `notebooks` folder:

```bash
notebooks/run-workflow.ipynb
```

This will:

- Run the full RAG pipeline
- Register the model in MLflow

### Step 2: Deploy the Chatbot Service

- Go to **Deployments > New Service** in AI Studio.
- Name the service and select the registered model.
- Choose a model version and enable **GPU acceleration**.
- Start the deployment.
- Once deployed, access the **Swagger UI** via the Service URL.
- From the Swagger page, click the demo link to interact with the locally deployed vanilla RAG chatbot via UI.

### Successful Demonstration of the User Interface

![Vanilla RAG HTML UI](docs/html_ui_for_vanilla_rag.png)

![Vanilla RAG Streamlit UI](docs/streamlit_ui_for_vanilla_rag.png.png)

---

## Contact and Support

- **Troubleshooting:** Refer to the [**Troubleshooting**](https://github.com/HPInc/AI-Blueprints/tree/main?tab=readme-ov-file#troubleshooting) section of the main README in our public AI-Blueprints GitHub repo for solutions to common issues.

- **Issues & Bugs:** Open a new issue in our [**AI-Blueprints GitHub repo**](https://github.com/HPInc/AI-Blueprints).

- **Docs:** [**AI Studio Documentation**](https://zdocs.datascience.hp.com/docs/aistudio/overview).

- **Community:** Join the [**HP AI Creator Community**](https://community.datascience.hp.com/) for questions and help.

---

> Built with ❤️ using [**HP AI Studio**](https://hp.com/ai-studio).
