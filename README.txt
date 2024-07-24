# GTP

## Ollama
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
