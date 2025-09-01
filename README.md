# Oh my! First project
Hi there! My name is Cristian, and I pretty much like doing everything. Here I plan to post my little dumb adventures while playing around with some technologies, pretty much whatever I feel like at the moment. See ya!

### Ollama but it is tiny tiny and local local (as is supposed to)
I have been using for the past 6 months an old computer as a server for different services (streaming, multimedia... I will talk about everything eventually here), and I am an AI enthusiast, so I got to think _what if I build my own little LLM so I can personalise it_? For example, I am omw to pursue a PhD; I could make a LLM specialized in its topic, etc. So I got around to work with it.

I have been learning lately machine learning, but have never deploy anything, nor work with complete autonomous systems, agents, or the _cool_ stuff the internet is talking about. So I am pretty new to all this world, just seen some blogs on MCP (all my love to Anthropic) and playing around with different models. 

#### Deployment
Easy peasy, to be honest. Just [searching around](https://hub.docker.com/r/ollama/ollama) I found the docker container to safely deploy and get running my little thing. In bash, copy paste the following code:
```
$ curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey \
    | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg
$ curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list \
    | sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' \
    | sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
$ sudo apt-get update
$ sudo apt-get install -y nvidia-container-toolkit
$ sudo nvidia-ctk runtime configure --runtime=docker
$ sudo systemctl restart docker
$ docker run -d --gpus=all -v ollama:/root/.ollama -p 11434:11434 --name ollama ollama/ollama
```
_et voilà!_ we have our LLM safely deployed. Last but not least, we have to select the model to play around. In my case I have gone with DeepSeek-R1-0528-Qwen3-1.5B cuz I want something little (my PC is 10 years old and working with a 750Ti wont take me that far way).
