#IMPORTANT MESSAGE : This repo will be moving into the -OMARG-AIR-AID repository to be adapted via the in repo OS.


# pepeai-testnet
- experimental testnet for decentralized p2p AI processing



Setting up the environment:

Nvidia Driver:
```
sudo apt-get update && sudo apt-get install nvidia-driver-530
```


Docker:
 - Linux
 - Windows
 - OSX

```
sudo docker run -p 31330:31330 --ipc host --gpus all --volume petals-cache:/cache --rm     learningathome/petals:main python -m petals.cli.run_server bigscience/bloomz-petals --initial_peers /ip4/54.164.52.79/tcp/8989/p2p/QmR7G6GZzeQeJoXfTovp8PJdJ7qxKYFwXUa2fp9p6BYdDi --port 31330
```

Or install manually:

Anaconda Install:

```
wget https://repo.anaconda.com/archive/Anaconda3-2023.03-1-Linux-x86_64.sh
chmod +x ./Anaconda3-2023.03-1-Linux-x86_64.sh
./Anaconda3-2023.03-1-Linux-x86_64.sh
```

Answer yes to base env setup.

```
conda create -n pepeaitestnet python=3.10
conda activate pepeaitestnet
conda install pytorch pytorch-cuda=11.7 -c pytorch -c nvidia
pip install -r requirements.txt
```

Running a Node:

PepeAI net seperates processing by PepeCoin Nodes.  Each node requires at least 1 GPU w/ 8GB+ or more of memory.

- bloom model layers distrubuted across fleet of pepecoin nodes
- will support various models as they are updated for pepecoin ai net


Start GPU Processing Node:
- ensure environment is setup as indicated above
- If you have more than 1 GPU, set the GPU index before starting the node
- you can run multiple nodes under screen
```
export CUDA_VISIBLE_DEVICES=0  # Insert the GPU index here, counting from zero
python -m petals.cli.run_server bigscience/bloomz-petals --initial_peers /ip4/54.164.52.79/tcp/8989/p2p/QmR7G6GZzeQeJoXfTovp8PJdJ7qxKYFwXUa2fp9p6BYdDi
```

Demo Chatbot:
```
python3 ./pepeaichatbot.py
```

