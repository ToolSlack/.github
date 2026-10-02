# ToolSlack: Exploiting Tool Execution Windows for Efficient LLM Agent Serving

<p align="center"><img src="https://github.com/ToolSlack/ToolSlack/blob/HEAD/assets/toolslack-logo.png?raw=true" width="520" alt="ToolSlack"></p>

ToolSlack schedules agent memory and exact-prefix KV preparation during real tool
execution. The anonymous artifact includes the dense Qwen3-8B / LangGraph / LangMem
implementation, CPU correctness checks, and a native GPU benchmark workflow.

[Code and reproduction instructions](https://github.com/ToolSlack/ToolSlack)

## Quick start

```sh
git clone https://github.com/ToolSlack/ToolSlack.git
cd ToolSlack
./run.sh cpu
```

The CPU command bootstraps the pinned environment and runs correctness checks on
Linux or macOS. Python 3.9 or newer is required to start it; no API key, model
weights, CUDA installation, or GPU allocation is needed.

For the native GPU workflow, first read the
[hardware and reproduction prerequisites](https://github.com/ToolSlack/ToolSlack#one-command-gpu-smoke-and-benchmark).
Use Linux x86_64 with one independently reserved, empty GPU, and replace `0` with
its physical `nvidia-smi` index:

```sh
./run.sh smoke --gpu-indices 0 --exclusive-gpus
./run.sh full --gpu-indices 0 --exclusive-gpus
```

CPU validation does not establish GPU performance. Fresh native-engine
installation, GPU smoke, native DMA correctness, and paper performance
reproduction remain unverified; see the
[validation status and scope](https://github.com/ToolSlack/ToolSlack#reproduction-scope-and-interpretation).
