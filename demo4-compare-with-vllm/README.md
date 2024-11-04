
# Sharing KV cache across different vLLMs

## Brief introduction

This demo shows that different vLLM instances can share the prefix KV cache between each other by using LMCache on a single node, so that the KV cache generated by one vLLM instance can be reused by another.

Note that though this demo focuses on single-node case, it can be generalized to allow KV cache sharing between any two vLLM instances in the cluster, as long as they have a commonly-shared NFS disk.

## Setup instructions

### Prerequisites
- 4 Nvidia A6000 or A40 GPU on the same node
- Local SSD disk with peak IO bandwidth > 3GB/s
- `docker compose` installed on the machine
- sudo access to run `docker compose up`
- A huggingface token with access to `mistralai/Mistral-7B-Instruct-v0.2`. 


#### Customizing this demo

Note that this demo runs the model `mistralai/Mistral-7B-Instruct-v0.2` and stores KV cache under directory `/tmp`. You can customize these two entires by editing the file `.env` under `demo4-compare-with-vllm`.

### Run this demo

Run the following bash scripts:
```
git clone https://github.com/LMCache/demo.git
cd demo/demo4-compare-with-vllm
echo "HF_TOKEN=<your HF token>" >> .env
docker compose up
```
Please replace `<your HF token>` with your huggingface token in the bash script above.


## Expected results
