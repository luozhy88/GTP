# GTP

## Ollama
nvidia-smi --query-gpu=utilization.gpu,memory.used --format=csv # GPU 使用情况

### install
https://github.com/jmorganca/ollama/blob/main/docs/linux.md
sudo nano /etc/systemd/system/ollama.service  
CPUQuota=3000%  
sudo systemctl daemon-reload  
sudo systemctl restart ollama  

### models
https://ollama.ai/library  

ollama run mixtral
## perplexity
https://labs.perplexity.ai/
## claude 
https://claude.ai/
## search.sciphi.ai
https://search.sciphi.ai/

## AI
https://www.toolify.ai/zh

## ChatGPTNextWeb
https://github.com/ChatGPTNextWeb/ChatGPT-Next-Web/tree/main

https://github.com/binary-husky/gpt_academic/

https://igdux.com/ai3


# 查看KEY额度
https://kapkey.chatgptapi.org.cn/


# 本地加载大模型
https://mp.weixin.qq.com/s/ONHcYiF3FyqiIBcWN0QrNA    
https://docs.openwebui.com/getting-started/troubleshooting/    
docker run --network=host -it  -p 3000:8080 --add-host=host.docker.internal:host-gateway  -v open-webui:/app/backend/data --name open-webui  ghcr.io/open-webui/open-webui:main   
docker run -d --ulimit nproc=30  -p 3000:8080 --add-host=host.docker.internal:host-gateway  -v open-webui:/app/backend/data --name open-webui  ghcr.io/open-webui/open-webui:ollama  


##--restart always   
##--add-host=host.docker.internal:host-gateway  
##-e OLLAMA_API_BASE_URL=http://192.168.30.202:11434   

页面：IP:8080  
软件管理页面设置：  Connections:  http://localhost:11434    


# ollamar 在R中掉用
library(ollamar)
test_connection()  # test connection to Ollama server; returns a httr2 response object
# Ollama local server running
# <httr2_response>

list_models()  # list available models (models you've pulled/downloaded)
pull("qwen")  # pull/download llama3 model
resp <- generate("qwen:1.8b", "你是谁")  # return httr2 response object by default
resp
pp=generate("qwen:1.8b", "你是谁", output = "text")

# 镜像中调GPU方式
https://www.jianshu.com/p/0d10b821d5c1
nvtop
https://ollama.com/install.sh


#################################### 大模型微调#######################################
# 大模型下载
git clone https://opencsg.com/models/shareAI/llama3-Chinese-chat-8b.git --depth 1
git clone https://opencsg.com/models/AIWizards/Llama3-8B-Chinese-Chat.git
git clone https://www.modelscope.cn/qwen/Qwen2-7B-Instruct.git
git clone https://www.modelscope.cn/qwen/Qwen2-1.5B.git

sudo apt install git-lfs
git lfs pull

# 大模型训练
llamafactory-cli train examples/train_lora/llama3_lora_pretrain.yaml
llamafactory-cli chat examples/inference/llama3_lora_sft.yaml
llamafactory-cli export examples/merge_lora/llama3_lora_sft.yaml

# 安装模型转换工具
git clone https://github.com/ggerganov/llama.cpp.git
cd llama.cpp
make
pip install -r requirements.txt

/home/zhiyu/miniconda3/bin/python /mnt/zhiyu/data/software/llama.cpp-master/convert_hf_to_gguf.py /mnt/zhiyu/data/software/LLaMA-Factory/models/llama3_lora_sft --outfile /mnt/zhiyu/data/software/LLaMA-Factory/models/gguf

# 生成可用的模型
##Modelfile
# FROM /mnt/zhiyu/data/software/LLaMA-Factory/models/gguf/llama3-Chinese-8B-chat-F16.gguf
# PARAMETER temperature 0.7
# PARAMETER top_p 0.95
# SYSTEM You are a helpful AI assistant.

ollama create llama3_ceshi -f /mnt/zhiyu/data/software/LLaMA-Factory/models/gguf/Modelfile





https://huggingface.co/Rookie/Llama-3-8B-Instruct-Chinese
https://wisemodel.cn/models/shareAI/llama3-Chinese-chat-8b
https://opencsg.com/models/shareAI/llama3-Chinese-chat-8b #ok
https://ai.gitee.com/hf-models/meta-llama/Meta-Llama-3-8B-Instruct/tree/main
https://modelscope.cn/models/LLM-Research/Meta-Llama-3-8B-Instruct/files
https://github.com/Rookie1019/Llama-3-8B-Instruct-Chinese
#################################### 大模型微调#######################################


# 测试另外服务器是否能调用deepseek-coder
curl -X POST http://192.168.30.214:11434/api/generate -d '{
  "model": "deepseek-coder-v2:latest",
  "prompt":"Why is the sky blue?"
 }'

#####################################lisakim0 RAG#################################
A Retrieval-Augmented Generation (RAG) system for PDF document analysis using DeepSeek-R1 and Ollama. 
https://gist.github.com/lisakim0/0204d7504d17cefceaf2d37261c1b7d5


pip install -U langchain langchain-community --index-url https://pypi.tuna.tsinghua.edu.cn/simple 
pip install streamlit  --index-url https://pypi.tuna.tsinghua.edu.cn/simple #指定镜像源安装
pip install pdfplumber  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install semantic-chunkers  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install open-text-embeddings  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
conda install faiss 

pip install prompt-template  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install langchain  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install langchain_experimental  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
pip install sentence-transformers  --index-url https://pypi.tuna.tsinghua.edu.cn/simple
#pip install faiss-cpu  --index-url https://pypi.tuna.tsinghua.edu.cn/simple

pip install ollama 

###########################Dify
输入的模型名称必须是ollama中的模型名称
https://mp.weixin.qq.com/s/n5GrGZ9hZmdhzt4avs1XSw

# prompt
https://promptup.net/prompt/2dd96b9a-2284-4573-aedd-a0ec006db014



