# DDE-GPT: An AI Assistant for Documentation Generation

> Deep-time.org是一个一站式在线地球科学科研协作平台。秉承“链接”的核心理念，基于Deep-Time Engine深时探索引擎，链通全球科研要素，通过Resource Hub、Earth Explorer、Analysis、MyDDE、Global Layer五大核心模块，向用户提供强大的数据、知识、计算、场景能力。通过平台形式支撑云上数据驱动地学研究环境的构建，并促进全球科学家的链接与在线协作。目前平台已支撑了古地理重建、矿产资源预测等若干地学场景，未来平台将持续围绕大科学问题，以数据驱动研究为核心手段，支撑小尺度更好、大尺度更快、多学科交叉、多圈层复合的研究，实现深时四大演化的科研探索。

## Introduction

We introduce **DDE-GPT** , a chatrobot focusing on documentation generation for Deep-time.org plantform.

## Demo

Add a local doc into DDE-GPT and chat with it to generate report.

`DDE白皮书（英文）.docx` ~30MB

Chat in console without GUI.

**1. Prepare the code and the environment**

Clone our repository, create a Python environment, and activate it via the following command.

```bash
git clone https://github.com/Bili-Sakura/DDE-GPT
cd DDE-GPT
conda env create -f environment.yml
conda activate DDE-GPT
```

**2. Get access to OpenAI by purchasing api_key**

<a href='https://openai.com/pricing'><img src='./assets/openai_green.png' alt='OpenAI logo' style='width: 16px; height: 16px; vertical-align: middle;'> See OpenAI API Key Pricing</a>

Here, we recommend gpt-3 series base model, typically `gpt-3.5-turbo-0125`, which is capable and cost-effective,supporting a 16K context window and is optimized for dialog.
Here we list all the gpt-3 series base models, regarding to their model name, input cost and output cost.  
>Note: If you are going to use a multimodel, be it gpt-4, as your base model, you may overwrite the functions in `chat_bubble.py` to adapt the multimodel output.

| Model                  | Input Cost per 1K tokens | Output Cost per 1K tokens |
| ---------------------- | ------------------------ | ------------------------- |
| gpt-3.5-turbo-0125     | $0.0005                  | $0.0015                   |
| gpt-3.5-turbo-instruct | $0.0015                  | $0.0020                   |
| gpt-3.5-turbo-1106     | $0.0010                  | $0.0020                   |
| gpt-3.5-turbo-0613     | $0.0015                  | $0.0020                   |
| gpt-3.5-turbo-16k-0613 | $0.0030                  | $0.0040                   |
| gpt-3.5-turbo-0301     | $0.0015                  | $0.0020                   |
| gpt-3.5-turbo          | $0.0030                  | $0.0060                   |

**3. Set configurations of OpenAI**

Create a `.env` file in the root directory of DDE-GPT project. Add following configurations to enable your own LLMs.

```python
"""
Note: It is also availble to use other base model instead of OpenAI's gpt series. Following these steps:
1. Add configs for your LLMs base model in .env file.
2. Adapt the LLMs interface in src/llm.py.
3. If you are using an open-sourced LLMs base model such as LLaMA-2, it is required to download pre-trained model locally. Besides, running model locally requires better CPUs/GPUs. 
"""
# Replace the value with your own OpenAI API KEY.
OPENAI_API_KEY="sk-xxxx"
# Enable the base url config if your api key is transited.
# Otherwise, set as "".
OPENAI_BASE_URL="https://baseurl.example.com"
```

**4. Run `demo.ipynb`**