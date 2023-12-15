# RASA

## Introduction to RASA

* RASA** is an open-source conversational AI platform that allows developers to build and deploy natural language processing (NLP) based chatbots and virtual assistants. RASA is designed to handle both the natural language understanding (NLU) and the dialogue management aspects of conversational systems. It provides a flexible and customizable framework for creating context-aware and interactive conversational experiences.

### Key Features

- **Open Source:** RASA is open-source and can be freely used, modified, and extended by developers.
- **Flexibility:** RASA provides a high level of flexibility, allowing developers to customize and fine-tune the behavior of their conversational AI applications.
- **Context Management:** RASA Core maintains context and dialogue history to generate more contextually relevant responses.
- **Training:** Both RASA NLU and RASA Core are trainable, allowing developers to improve their performance with domain-specific data.
- **Multi-Channel Support:** RASA supports interactions across various channels, such as messaging platforms, websites, and more.
- **Scalability:** RASA is designed to scale, making it suitable for both small projects and large-scale applications.


## RASA Architecture Overview 

RASA is an open-source conversational AI platform that consists of two main components: RASA NLU and RASA Core. These components work together to enable the development of powerful and context-aware conversational applications.

### 1. RASA NLU (Natural Language Understanding):

**Purpose:**
- RASA NLU is responsible for understanding and extracting structured information from user messages.
- It helps in turning user inputs into structured data that can be easily understood by machines.

**Key Features:**
- **Intent Recognition:** Identifying the intention behind a user's message (e.g., "Book a Flight," "Get Weather Information").
- **Entity Extraction:** Extracting important entities or pieces of information from the user's message (e.g., Dates, Locations, Product Names).
- **Intent Classification:** Determining the primary goal or action the user wants to perform based on their input.

**Training Data:**
RASA NLU is trained on labeled examples of user messages, where intents and entities are annotated. It uses this training data to learn patterns and improve its ability to recognize intents and entities accurately.

**Pipeline Configuration:**
RASA NLU uses a pipeline-based approach for processing and interpreting user messages. A pipeline consists of different components, such as tokenizers, featurizers, and machine learning models, arranged in a sequence. Example: A typical pipeline might include a tokenizer to break the text into words, a featurizer to convert words into numerical features, and a machine learning model for intent and entity recognition

### 2. RASA Core (Now RASA Open Source):

**Purpose:**
- RASA Core is responsible for handling the dialogue flow and making decisions on how the assistant should respond to user inputs.
- It manages the conversation by predicting the next action to take based on the current state of the dialogue.

**Key Features:**
- **Dialogue Management:** Dialogue management involves predicting the next action to take in the conversation based on the user's input and the current state of the dialogue. Example: If the user asks about the weather, the dialogue manager may decide to trigger the "Get Weather" action.
- **Policy Learning:** RASA Core uses machine learning models (policies) to learn how to select actions in different situations. These policies are learned from example dialogues provided during training Example: By learning from example dialogues, RASA Core can understand when to ask for clarification, provide information, or take other actions.
- **Training Data:** Similar to RASA NLU, RASA Core is trained on example dialogues that include user inputs, system responses, and the corresponding actions taken by the assistant.

**Stories:**
Stories are example dialogues that help train the RASA Core model. They consist of user inputs, system responses, and the corresponding actions taken by the assistant. Example: A story might describe a user asking about the weather, the assistant responding with the weather information, and the action of sending the information to the user.

**Action Server:**
The Action Server is responsible for executing the actions predicted by RASA Core. These actions could include sending a message to the user, querying a database, or performing any other custom operation. Example: If the predicted action is "Get Weather," the Action Server would handle the logic to fetch the current weather from a relevant source.


## RASA SDK
The RASA SDK (Software Development Kit) is a set of tools and libraries that helps developers create and customize chatbots using the RASA framework.

**Key Components and Features of the RASA SDK:**
1. **Actions and Custom Actions:**
   - In RASA, actions are tasks that a bot can perform, such as fetching data from an external API, querying a database, or generating a response. Custom actions are user-defined actions that can be implemented using the RASA SDK.
   - The RASA SDK provides a convenient way to create custom actions by subclassing the Action class and implementing the run method. These actions can be used to execute custom code and generate dynamic responses.

2. **Action Server:**
   - The Action Server is a separate process that runs custom actions in response to user inputs. It communicates with the RASA Core (now RASA Open Source) server to perform actions triggered by user messages.
   - Developers need to run the Action Server alongside the RASA Core Server to handle custom actions.
  
3. **Custom Components:**
   - RASA allows developers to create custom components for different stages of the NLU (Natural Language Understanding) and dialogue management pipelines. These components can be used to extend or modify the default behavior of the RASA framework.
   - Custom components can be written in Python and integrated into the RASA pipeline to enhance the capabilities of the chatbot.
  
4. **Endpoints Configuration:**
   - The endpoints.yml file in a RASA project is used to configure various endpoints, including the endpoint for the Action Server. This file specifies the URL where the Action Server can be reached.

5. **Interactive Learning:**
   - The RASA SDK supports interactive learning, allowing developers to improve the model by providing feedback during conversations. This can be done using the RASA Interactive Command, which uses a simple interactive mode to correct and retrain the model based on user feedback.


## RASA X

* RASA X** is a tool designed to complement the RASA Open Source framework, providing a user interface for developers, product managers, and non-technical users to collaborate on the development and improvement of conversational AI models. It simplifies tasks such as training models, managing conversations, and improving the performance of your chatbot.

**Key Components and Features of the RASA X:**

1. **User Interface:**
   - RASA X provides a web-based user interface that allows users to interact with their chatbot, review conversations, and annotate training data without needing to work directly with code.

2. **Conversation Review:**
   - Users can review and annotate conversations to improve the training data and the performance of the model. This is particularly useful for fine-tuning the chatbot's responses and handling edge cases.

3. **Model Training:**
   - RASA X facilitates model training directly from the user interface. Users can train and evaluate models without having to use the command line, making it more accessible for non-technical team members.

4. **Version Control:**
   - RASA X includes version control features, allowing users to track changes to their NLU data, stories, and other configuration files. This helps in managing the evolution of the conversational AI model over time.

5. **Collaboration:**
   - RASA X supports collaboration among team members by allowing multiple users to work on the same project simultaneously. This is especially useful for teams working on chatbot development and maintenance.

6. **Integration with RASA Open Source:**
   - RASA X is tightly integrated with RASA Open Source. You can use RASA X to experiment with and improve your models, and then seamlessly transition to RASA Open Source for more advanced customization and development.



## RASA Project Structure

When initializing a RASA project, the directory structure includes the following folders and files:

- **actions:**
  - This directory is designated for storing custom action files. Actions in RASA are executable pieces of code that respond to user messages. For instance, an action might involve calling an external API or implementing specific custom logic.

- **credentials.yml:**
  - This file serves as a secure repository for storing sensitive information like API keys, passwords, or other credentials essential for the chatbot. It emphasizes the importance of safeguarding such information and avoiding exposure in the codebase.

- **domain.yml:**
  - The domain.yml file outlines the domain of your chatbot, encompassing details about intents, entities, actions, and responses. Essentially, it defines what the chatbot comprehends and how it should respond to various user inputs.

- **tests:**
  - This folder is dedicated to housing test cases for the chatbot. Thorough testing ensures that the chatbot functions as expected and adeptly handles diverse scenarios.

- **config.yml:**
  - Contained within this file are configuration settings for both Rasa NLU (Natural Language Understanding) and Rasa Core models. It specifies the pipeline for processing user messages and other pertinent settings related to model training.

- **data:**
  - This folder typically houses training data for the chatbot, including examples of user messages, intents, entities, and corresponding responses. The training data is instrumental in training both the NLU and Core models.

    - **Subfiles of "data"**

      - **nlu.yml:**
         - This file holds training examples for the Natural Language Understanding (NLU) module of the chatbot. It includes user message examples with corresponding intents and entities, with the NLU model responsible for understanding and extracting meaning from user input.

      - **rules.yml:**
         - The rules.yml file defines conversation rules for the chatbot. These rules specify behaviors based on certain conditions, often tied to detected intents and entities in user messages. Rules play a crucial role in directing the flow of the conversation.

      - **stories.yml:**
        - Containing conversational stories, this file represents potential interactions between users and the chatbot. Each story comprises a sequence of user messages, bot responses, and potential actions. These stories are employed in training the RASA Core Model, which dictates the dialogue flow of the chatbot.

- **endpoints.yml:**
  - This file outlines the endpoints for the chatbot, such as the location of the Rasa Core server and any external services or APIs the chatbot may interact with. It aids in configuring connections between different components.

- **models:**
  - After training the chatbot, the resulting trained models are stored in this folder. These models include both the NLU model, responsible for understanding user input, and the Core model, determining the chatbot's response strategies.