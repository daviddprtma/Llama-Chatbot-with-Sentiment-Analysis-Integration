
<br/>
<div align="center">

<h3 align="center">Mental Health Assistant</h3>
<p align="center">
A compassionate and supportive chatbot designed to provide users with emotional support and encouragement. Utilizing advanced sentiment analysis powered by Hugging Face's AI


  


</p>
</div>

## Why Mental Health Assistant? ✅

![Product Screenshot](https://github.com/daviddprtma/Llama-Chatbot-with-Sentiment-Analysis-Integration/blob/8b65bb1070441362eacfd115b985af2364145ca2/mental%20health%20assistant.png)

Mental Health Assistant is a compassionate and supportive chatbot designed to provide users with emotional support and encouragement. Utilizing advanced sentiment analysis powered by Hugging Face's AI models, this assistant can detect when users are feeling down or expressing negative emotions.

Key Features:
- Sentiment Detection: The assistant analyzes user input to identify emotional states, allowing it to respond appropriately to feelings of sadness, anxiety, or distress.
- Uplifting Responses: When negative sentiments are detected, the chatbot offers comforting and encouraging messages, reminding users that they are not alone and that it's okay to seek help.
- Positive Reinforcement: For users expressing positive feelings, the assistant reinforces this positivity with affirmations and encouragement to maintain a healthy mindset.
- User-Friendly Interface: Built with Gradio, the chatbot features an intuitive interface that makes it easy for users to interact with the assistant in a conversational manner. 

Purpose:

Mental Health Assistant aims to provide immediate emotional support, promote mental well-being, and foster a sense of connection. It serves as a helpful resource for individuals seeking comfort, guidance, or simply a friendly conversation about their feelings. This tool is particularly beneficial in applications focused on mental health support, making it accessible to anyone who may need a listening ear.

In here, I will assist step by step about how you can talk to Mental Health Assistant by ask to the bot according to your mood and the Chatbot will give you the answer according to your mood.


### Built With

- [Python](https://www.python.org/)
- [Google Colab](https://colab.research.google.com/)
- [Hugging Face](https://huggingface.co/)
## Getting Started

Before you can use this project, you must follow the requirements here
### Prerequisites

1. Open your Google Colab and create a new project. 

2. Before to run, make sure you connect and choose T4 GPU by clicking connect dropdown, choose change run time, choose hardware accelerator from CPU to T4 GPU to make a model faster to load. And afterthat, click save. 

3. Install Required Libraries
Run the following code to install the necessary libraries:

  ```sh
  !pip install transformers torch gradio
  ```

4. Import Libraries
Import the required libraries:

 ```sh
import torch
from transformers import pipeline
import gradio as gr
  ```

5. Load the Sentiment Analysis Model
Load a pre-trained sentiment analysis model from Hugging Face:

 ```sh
sentiment_analysis = pipeline("sentiment-analysis")
  ```

6. Define the Chatbot Logic
Create a function that detects the user's sentiment and provides uplifting messages:

 ```sh
def mental_health_chatbot(user_input):
    # Analyze the sentiment of the user input
    result = sentiment_analysis(user_input)[0]

    # Check the sentiment
    if result['label'] == 'NEGATIVE' and result['score'] > 0.5:
        response = "I'm really sorry to hear that you're feeling this way. Remember, it's okay to ask for help. You're not alone!"
    elif result['label'] == 'POSITIVE':
        response = "That's great to hear! Keep up the positive mindset. Remember to take care of yourself!"
    else:
        response = "Thank you for sharing your thoughts. I'm here to listen if you want to talk more."

    return response
  ```

7. Create Gradio Interface
Set up the Gradio interface for user interaction:

 ```sh
def chat_interface(user_input):
    return mental_health_chatbot(user_input)

# Create the Gradio interface
iface = gr.Interface(
    fn=chat_interface,
    inputs="text",
    outputs="text",
    title="Mental Health Assistant",
    description="A chatbot that detects when you are feeling down and provides uplifting and supportive messages."
)

# Launch the interface
iface.launch()
  ```

And run the code from above so you can use this project by do click run in the google colab one by one.

## License

Distributed under the BSD 2-Clause "Simplified" License. See [BSD 2-Clause "Simplified" License](https://opensource.org/license/bsd-2-clause) for more information.
