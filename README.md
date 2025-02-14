# ComfyUI-Ollama-Describer

This is an extension for [ComfyUI](https://github.com/comfyanonymous/ComfyUI) that makes it possible to use some LLM models provided by Ollama, such as Gemma, Llava (multimodal), Llama2, Llama3 or Mistral. Speaking specifically of the LLaVa - Large Language and Vision Assistant model, although trained on a relatively small dataset, it demonstrates exceptional capabilities in understanding images and answering questions about them. This model presents similar behaviors to multimodal models such as GPT-4, even when presented with invisible images and instructions.

For more information about the LLaVa model, visit: [LLaVa Model Website](https://llava-vl.github.io/)

![alt text](image.png)

## Requirements

To use this extension, you will need the Ollama library, which facilitates the use of large-scale language models (LLMs). Ollama provides a simple and efficient interface for interacting with these models, including facilitating the use of GPUs using CUDA (NVIDIA). It also supports AMD GPUs.

Ollama is currently available for installation on Windows, Linux, and Mac. Additionally, you can run Ollama using Docker. In both cases, if you want to use your NVIDIA GPUs to speed up processing, you need to install the NVIDIA CUDA Toolkit.

Follow the guide on the Ollama website and install according to your operating system or opt for usage through a Docker container.

- [Ollama Website](https://ollama.com/)
- [Ollama Docker Hub](https://hub.docker.com/r/ollama/ollama)
- [Ollama GitHub Repository](https://github.com/ollama/ollama)
- [Ollama GPU Installation Guide](https://github.com/ollama/ollama/blob/main/docs/gpu.md)

## Installation

1. Install and Run Ollama
    - [Ollama Website](https://ollama.com/)

2. Clone the repository into your `custom_nodes` folder:
    ```bash
    git clone https://github.com/alisson-anjos/ComfyUI-Ollama-Describer.git
    ```
   The path should be something like `custom_nodes\ComfyUI-Ollama-Describer`.
   
3. Open the folder and execute `install.bat` (Windows) or open a terminal in the folder and run:
    ```bash
    pip install -r requirements.txt
    ```
After installing Ollama and getting it running, you can use the extension in your ComfyUI.

## Usage
### LlaVa Describer
Add the node via `Ollama` -> `LlaVa Describer`  

![alt text](image-2.png)

- **model**: Select one of the models, 7b, 13b or 34b, the greater the number of parameters in the selected model the longer it will take to execute the prompt and return the response, use according to the capabilities of your hardware. For most users, I recommend using the 7b/13b model as it offers a good balance between performance and resource requirements.
- **api_host**: With this parameter you can specify the address of the API used to communicate with the model, you can use it locally (localhost..) or remotely. Remembering that to run ollama locally, it must be running on your machine.
- **timeout**: With this parameter you can specify the maximum response time, if the time exceeds this value the request will be cancelled.
- **temperature**: The higher this value, or closer to 1, the more creative/random the answer will be. In other words, the model may not follow the instructions added in your prompt or even add false information, the LLaVa model provides good answers with temperatures from 0.2 and below.
- **seed_number**: Sets the random number seed to use for generation. Setting this to a specific number will cause the template to generate the same text for the same prompt. The default value is 0, to set a random seed set -1.
- **max_tokens**: Maximum length of response, in tokens. A token is approximately half a word.
- **keep_model_alive**: This parameter is used to define how long the model will remain in memory after generation
    - 0 means the model will not remain loaded.
    - -1 means it will stay loaded indefinitely and keep_alive.
    - any other value (e.g. 5, 10, or 20) will keep the model loaded for that amount of time in seconds after generation (always put the value in seconds).
    
    Note: the last node executed is the one that will set the final value for keep_model_alive. Example if you have 3 nodes with different keep_model_alive, the last one executed is the value that will persist.
- **prompt**: Text provided to the model containing a question or instruction.
- **system_context**: This parameter is used to provide a specific context to the model, directly influencing the responses generated by the model. This context is crucial to ensuring that answers are relevant and aligned with the context of the query, even when there is no specific “correct” answer available. (optional)

### Ollama Describer

Add the node via `Ollama` -> `Ollama Describer`  

![alt text](image-1.png)

- **model**: Select one of the available models: Gemma, Llama2, Llama3, or Mistral. Keep in mind that models with a larger number of parameters (e.g., 2b, 7b, 8b, 13b, 70b) are larger in size (gigabytes) and require more powerful hardware to run efficiently. Choose a model that matches the capabilities of your hardware. For most users, I recommend using the 7b/13b model as it offers a good balance between performance and resource requirements.
- **api_host**: With this parameter you can specify the address of the API used to communicate with the model, you can use it locally (localhost..) or remotely. Remembering that to run ollama locally, it must be running on your machine.
- **timeout**: With this parameter you can specify the maximum response time, if the time exceeds this value the request will be cancelled.
- **temperature**: The higher this value, or closer to 1, the more creative/random the answer will be. In other words, the model may not follow the instructions added in your prompt or even add false information, the LLaVa model provides good answers with temperatures from 0.2 and below.
- **seed_number**: Sets the random number seed to use for generation. Setting this to a specific number will cause the template to generate the same text for the same prompt. The default value is 0, to set a random seed set -1.
- **max_tokens**: Maximum length of response, in tokens. A token is approximately half a word.
- **keep_model_alive**: This parameter is used to define how long the model will remain in memory after generation
    - 0 means the model will not remain loaded.
    - -1 means it will stay loaded indefinitely and keep_alive.
    - any other value (e.g. 5, 10, or 20) will keep the model loaded for that amount of time in seconds after generation (always put the value in seconds).
    
    Note: the last node executed is the one that will set the final value for keep_model_alive. Example if you have 3 nodes with different keep_model_alive, the last one executed is the value that will persist.
- **prompt**: Text provided to the model containing a question or instruction.
- **system_context**: This parameter is used to provide a specific context to the model, directly influencing the responses generated by the model. This context is crucial to ensuring that answers are relevant and aligned with the context of the query, even when there is no specific “correct” answer available. (optional)




