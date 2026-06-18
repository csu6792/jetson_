# jetson_

## Build llama.cpp

```cd ~
git clone https://github.com/ggml-org/llama.cpp.git
cd llama.cpp
cmake -B build \
  -DGGML_CUDA=ON \
  -DCMAKE_CUDA_ARCHITECTURES="87" \
  -DGGML_NATIVE=ON \
  -DCMAKE_BUILD_TYPE=Release
cmake --build build --config Release -j4
```

## Download the model and vision projector

```mkdir -p ~/models && cd ~/models

wget -O gemma-4-E2B-it-Q4_K_M.gguf https://huggingface.co/unsloth/gemma-4-E2B-it-GGUF/resolve/main/gemma-4-E2B-it-Q4_K_M.gguf

wget -O mmproj-gemma4-e2b-f16.gguf https://huggingface.co/ggml-org/gemma-4-E2B-it-GGUF/resolve/main/mmproj-gemma-4-E2B-it-bf16.gguf
```

## Start the server
```CC=/usr/bin/gcc CXX=/usr/bin/g++ cmake -B build \
  -DGGML_CUDA=ON \
  -DCMAKE_CUDA_ARCHITECTURES="87" \
  -DGGML_NATIVE=ON \
  -DCMAKE_BUILD_TYPE=Release \
  -DCMAKE_CUDA_COMPILER=/usr/local/cuda/bin/nvcc
```
