# Workshop - Insurance Claims Processing

Link: https://demo.redhat.com/workshop/87caa7

Username: 

Password: 

## Workshop Overview
This lab will demonstrate how the combination of various Artificial Intelligence/Machine Learning (AI/ML) technologies can generate a valuable solution for a business problem. The information, code, models, and techniques presented illustrate how an initial prototype could be developed and do not represent the only way to meet the established requirements.

In addition to the training done for claims analysis, as part of the Workshop at TDC Florianópolis, the example has been adapted to use Skupper as the connection for private insurance claim data. With this, the solution will be implemented as follows:

1. The storage of raw claim data will be done within the company, ensuring data confidentiality and control.
2. A Go application will expose the internal data in a podman container with an endpoint for connection to Skupper. [go-flp(https://github.com/rafaelvzago/go-flp)
3. The environment for training AI/ML models will be set up in an Openshift AI cluster on AWS.
4. The connection between the podman data exposure service and the Openshift AI cloud environment will be established using Red Hat Service Interconnect (Skupper), which is a hybrid and multicloud application integration platform that allows connecting applications and data in any environment, whether on-premises, in the cloud, or in containers.

Details:

1. This workshop is based on a demonstration of OpenShift AI, which provides a complete working environment for AI/ML projects.
2. Project repository: [Insurance Claim Processing](https://github.com/rh-aiservices-bu/insurance-claim-processing/tree/main)
3. Red Hat Service Interconnect: [Red Hat Service Interconnect](https://www.redhat.com/en/technologies/cloud-computing/service-interconnect)
4. Skupper: [Skupper](https://skupper.io/)
5. Go-flp: [go-flp](https://github.com/rafaelvzago/go-flp)



![solucao](solucao.png)

## Process Structure

* Context
* Connection and Setup
* LLM
* Image Processing
* Web App
* Productization

## Scenario

We are a large multinational insurance company undergoing digital transformation, aiming to modernize practices and utilize new technologies. A small team has been tasked with analyzing the current claims process and proposing improvements.

The findings will be presented to the board of directors, and if convincing, the team will receive resources to implement the recommendations. The next sections of this chapter present the materials that were presented to the board.

We have the need to integrate the text analysis solution for claims processing with our API in a Kubernetes cluster on AWS, as the processing was done within another datacenter of the company.



## Challenges:

1. Maintaining data integrity and information security.
2. Email processing should be done with OpenShift AI in the datacenter located within the company.
3. The application containing sensitive data, such as original claims, should be kept within the company.
4. The connection between the data service and the datacenter should be secure.

## Analysis of the Current Claims Process

Claims can be received through various channels (email, fax, phone, web form), but they all need to be transcribed into the web form for standardization.

The processing is done by experts (humans), who take an average of 7 hours per claim. It is estimated that human errors cause losses of $2.5 million/year, and frauds, an additional $3.5 million/year.

There are many inefficiencies, such as "workload fatigue," which leads experts to make mistakes due to the repetitive nature of the work. Additionally, training new experts in the company's specific policies is time-consuming.

Encoding some of this knowledge into software is highly desirable.

## Proposed Improvements

**Recommendations:**

* Progressive and gradual implementation.
* Use AI/ML tools and techniques to assist experts (instead of completely replacing them).
* Provide support for repetitive and low-level tasks.
* Identify areas that need revision.
* Aid in data analysis and extraction.

**Objectives:**

* Reduce the average processing time from 7 hours per claim to 2 hours per claim.
* Reduce human error by 80%.
* Improve fraud detection by 25%.

**Requirements:**

* Measure performance more accurately, both at the beginning and after each change/improvement.

## Prototyping Work Examples

The examples below illustrate what we expect to achieve with the prototype version of the enhanced process.

### Using LLM for Text Summarization

Allows for faster reading by the expert.
![Image of text summary LLM](text-summary-LLM.png)

The image demonstrates how a language model (LLM) can summarize a long and confusing email from a customer about a car accident into a clear and concise format. This allows the insurance expert to quickly understand the key details of the accident (date, location, damages, witnesses), streamlining the claim analysis and processing.


### Using an LLM for Information Extraction

Allows for extracting key information from an email and automatically filling it in.

![Image of Information Extraction](information-extraction-LLM.png)

The image demonstrates how a language model (LLM) can extract key information from an email about a car accident and automatically fill in a structured form. In the example, the LLM correctly extracted the accident date, location, type of incident, and car model from the sender, saving time and reducing the risk of manual errors in incident registration.

## Prototyping Work Examples (Continuation)

### Using an LLM for Sentiment Analysis

Allows for quickly identifying customer sentiment.

![Image of Sentiment Analysis](sentiment-LLM.png)

Detect the tone of the text and potentially take action based on it.

## Results

The board of directors was convinced! The company has decided to fully fund the project, allowing the transition from the prototyping phase to production. And the good news is that you have been hired to be part of the team that will build and implement the complete solution!


### Architecture Overview

The image demonstrates the architecture of a computing cluster for data processing and artificial intelligence. The cluster consists of:

* **Shared Resources:**
    - ic-shared-minio: Object storage (MinIO) for data and artifacts.
    - ic-shared-app: Shared application for user interaction.
    - ic-shared-img-det: Image detection models.
    - ic-shared-db: Shared database.
    - ic-shared-llm: Large language models (LLMs) for natural language processing.

* **Individual Resources per User:**
    - Workbench: Development environment for each user (user1, user2, user3, ..., userN).
    - Model Serving: Service for deploying machine learning models.
    - Pipeline Server: Server for orchestrating data and machine learning pipelines.
    - Web App: Web application for user interaction.

* **Infrastructure:**
    - Multiple processing nodes with GPUs for executing computationally intensive tasks.
    - One dedicated GPU node for specific tasks.

The architecture allows multiple users to work on their own projects, utilizing shared and individual resources, with the support of a powerful computing infrastructure.

## How to Use LLMs?

- [Notebook for Using LLM](https://github.com/rh-aiservices-bu/insurance-claim-processing/blob/main/lab-materials/03/03-01-nb-llm-example.ipynb)

This notebook explores the programmatic interaction with a large language model (LLM), such as ChatGPT, using Python and the Langchain framework. Instead of using a graphical interface, we access the Mistral-7B Instruct v2 model directly through its API, leveraging its capabilities for specific tasks.

We configure the model with parameters like maximum number of tokens and temperature, which influence the length and creativity of the response. Additionally, we define a template with detailed instructions to guide the model's behavior, ensuring safe, ethical, and informative responses.

Using Langchain, we combine the model and the template to create a conversation object, which facilitates communication with the LLM. To demonstrate the interaction, we ask a question about Artificial Intelligence and receive a detailed and enlightening response from the model.

This programmatic process of interacting with LLMs opens up a range of possibilities to integrate language models into applications and systems, enabling the development of more personalized and efficient solutions.

### Notebook for Text Summarization

- [Notebook for Text Summarization with LLM](https://github.com/rh-aiservices-bu/insurance-claim-processing/blob/main/lab-materials/03/03-02-summarization.ipynb)

This Python code snippet prepares the data for summarizing claims using a language model (LLM). It reads all the JSON files in the 'claims' folder, which contain information about insurance claims. Then, it converts the content of each file into a Python dictionary and stores these dictionaries in a larger dictionary called `claims`. Each key in this dictionary is the name of the JSON file, and the corresponding value is the Python dictionary representing the claim.

Next, the code uses the Langchain framework to create a summarization pipeline. This pipeline combines the Mistral-7B Instruct v2 language model with a template that provides specific instructions for the summarization task. The goal is to generate concise and informative summaries for each claim present in the JSON files.

After creating the pipeline, the code iterates over each claim in the `claims` dictionary. For each claim, it displays the subject and original content of the claim, followed by the summary generated by the LLM. This allows for comparing the original text with the summary, evaluating the quality and usefulness of the summarization performed by the model.


### Notebook for Information Extraction

- [Notebook for extracting information with LLM](https://github.com/rh-aiservices-bu/insurance-claim-processing/blob/main/lab-materials/03/03-03-information-extraction.ipynb)

This notebook explores the ability of a Large Language Model (LLM) to analyze texts and extract specific information, such as the author's sentiment and details about an event.

Using the Langchain framework and the Mistral-7B Instruct v2 language model, an analysis pipeline is created. A specific template is defined to guide the LLM in extracting relevant information, such as the author's sentiment, location, and time of an event described in a text.

The code reads JSON files containing examples of insurance claims, and for each claim:

1. Displays the subject and original content of the message.
2. Performs three queries to the LLM:
    - Sentiment analysis: Detects the emotional state of the message author.
    - Location extraction: Identifies the location of the event mentioned in the message.
    - Time extraction: Determines the time (date and hour) of the event mentioned in the message.
3. Presents the analysis results, including the extracted sentiment, location, and time.

This demonstration illustrates how LLMs can be used to automate text analysis, extracting relevant information quickly and efficiently, which can be applied in various areas such as customer feedback analysis, content moderation, and document processing.

### Notebook for comparing LLM models

- [Notebook for comparing LLM models](https://github.com/rh-aiservices-bu/insurance-claim-processing/blob/main/lab-materials/03/03-04-comparing-models.ipynb)

This notebook explores the comparison between two language models (LLMs): Mistral-7B and Flan-T5-Small, evaluating their performance in text analysis tasks such as identifying the author's sentiment, location, and time of an event.

**Model Comparison:**

* **Mistral-7B:**
    - Larger model with 7 billion parameters.
    - Requires GPU with 24GB of RAM.
    - Provides more accurate and detailed text analysis results.
* **Flan-T5-Small:**
    - Smaller model with 80 million parameters.
    - Runs without GPU and with only 1GB of RAM.
    - Faster but with less precise and detailed results.

**Case Analysis:**

> The notebook demonstrates the analysis of a car claim using both models. Mistral-7B correctly identifies the sender's positive sentiment, the location (Birch Street and Willow Avenue intersection in Evergreen), and the time (January 2, 2024, at 3:30 PM). On the other hand, Flan-T5-Small provides inaccurate results, such as negative sentiment and incorrect information about the location and time.

**Conclusion:**

> The choice of the ideal model depends on the balance between performance, accuracy, and available resources. Mistral-7B offers higher accuracy but requires more resources. Flan-T5-Small is faster and lighter but less precise. It is crucial to perform sanity checks to ensure that the chosen model meets expectations and adapts to changes in the data.

### Modifying LLM Parameters

#### Exploring Settings and Modifying Data

To better understand the behavior of language models (LLMs), let's experiment with their settings and data.

**Adjusting LLM Settings:**

1. **Notebook 03-01-nb-llm-example.ipynb:**
   - Modify parameters like temperature for more creative responses.
   - Experiment with the prompt template to get responses in different formats (poems, explanations for specific audiences).
   - Change the questions to test robustness against "prompt injection".

**Modifying Data and Prompt:**

2. **Notebook 03-02-summarization.ipynb:**
   - Edit or create more complex claims.
   - Experiment with different languages.
3. **Notebook 03-03-information-extraction.ipynb:**
   - Edit or create more complex claims.
   - Adjust the prompt for more accurate date and time extraction in a specific format.

## Part 2: Hands On

### Activities

1. Install Skupper locally.
2. Install Skupper on the OpenShift Cluster.
3. Link the sites.
4. Run the application within the podman site and expose the service.
5. Execute the workshop with the modified examples [insurance-claim-processing-rafalvzago](https://github.com/rafaelvzago/insurance-claim-processing.git)

1. Installing Skupper on the podman site

```bash
export SKUPPER_PLATFORM=podman
podman network create skupper
./skupper init --ingress none
```

2. Install Skupper on the OpenShift Cluster

```
./skupper init --enable-console --enable-flow-collector --console-user admin --console-password admin
```

3. Linking the sites

* Creating the token on the more exposed cluster
    
    ```bash
    # skupper token create <token-name>
    ./skupper token create /tmp/insurance-claim
    ```
* Linking the podman site to the more exposed cluster
    
    ```bash
    # skupper link create <token-name> --name <site-name>
    ./skupper link create /tmp/insurance-claim --name ai
    ```

4. Running the application within the podman site and exposing the service

#### Running the application:

```bash
# podman run -d --network <network-name> -p <port>:<port> -v <volume with insurance claim files> --name <container-name> <image>
podman run -d --network skupper -p 8080:8080 -v /home/rzago/Code/go-flp/data:/app/data --name insurance-claim-data quay.io/rzago/insurance-claim-data:latest
```

##### Creating the service on the podman site:

> In this step, the service is created on the podman site and skupper will bind the service with the cluster service.

```bash
# skupper service create <service-name> <port>
./skupper service create backend 8080
```

> Binding the podman site service with the local service.


```bash
# skupper service bind <service-name> <target-name> --target-port <port>
./skupper service bind backend host insurance-claim-data --target-port 8080
```

##### Creating the service within the cluster to expose the service to the OpenShift cluster.

```bash
# skupper service create <service-name> <port>
./skupper service create backend 8080
```

5. Continue with the workshop until generating the email sentiments.