Documentation Negotiation Based Bot:
Objective: Create a chatbot that simulates a negotiation process between a customer and a supplier, leveraging pre-trained models like Gemini, ChatGPT, or other AI language models.

Code: (Coded on google golab)

Pip install openai
Pip install gradio

Import openai
Import gradio as gr

# Set your OpenAI API key
openai.api_key = "MY_api"

# Initialize the negotiation conversation
messages = [{"role": "system", "content": "You are a negotiation bot for a supplier. Negotiate with the customer and try to reach an agreement on the price."}]

# Function to simulate negotiation
def CustomChatGPT(user_input):
    # Append user input to the conversation
    messages.append({"role": "user", "content": user_input})

    # Call the OpenAI API to generate a response
    response = openai.ChatCompletion.create(
        model="gpt-3.5-turbo",  # You can also use 'gpt-4' if available
        messages=messages
    )

    # Extract the chatbot's response
    ChatGPT_reply = response["choices"][0]["message"]["content"]

    # Append the assistant's response to the conversation history
    messages.append({"role": "assistant", "content": ChatGPT_reply})

    # Return the assistant's response
    return ChatGPT_reply

# Example initial negotiation prompt
def start_negotiation():
    return "Welcome! Let's start the negotiation. What price are you willing to offer for the product?"

# Create a Gradio interface for user interaction
demo = gr.Interface(
    fn=CustomChatGPT, 
    inputs="text", 
    outputs="text", 
    title="Negotiation Bot",
    description="This bot helps you negotiate product prices."
)

# Launch the Gradio app with a welcome message
print(start_negotiation())
demo.launch()


 

If user says they don’t want to negotiate, it will show error since bot is made for negotiation and if we put invalid value it will show error.

 
If user initiate negotiation they bot will negotiate such that it tries to make maximum profit

 
User changed the price

 

GitURL: https://github.com/PriyadarshaniAwasthi/Negotiation-chatBot.git
