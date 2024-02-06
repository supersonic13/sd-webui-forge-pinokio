{
  "cmds": {
    "nvidia": "pip install torch torchvision torchaudio xformers --index-url https://download.pytorch.org/whl/cu121",
    "amd": "pip install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/rocm5.6",
    "default": "pip3 install --pre torch torchvision torchaudio --index-url https://download.pytorch.org/whl/nightly/cpu"
  },
  "requires": [{
    "type": "conda",
    "name": "ffmpeg",
    "args": "-c conda-forge"
  }],
  "run": [{
    "method": "shell.run",
    "params": {
      "message": "git clone https://github.com/lllyasviel/stable-diffusion-webui-forge.git app"
    }
  }, {
    "method": "shell.run",
    "params": {
      "venv": "env",
      "path": "app",
      "message": [
        "{{(gpu === 'nvidia' ? self.cmds.nvidia : (gpu === 'amd' ? self.cmds.amd : self.cmds.default))}}",
        "pip install -r requirements.txt"
      ]
    }
  }, {
    "method": "fs.share",
    "params": {
      "drive": {
        "checkpoints": "app/models/Stable-diffusion",
        "clip": "app/models/clip",
        "clip_vision": "app/models/clip_vision",
        "configs": "app/models/configs",
        "controlnet": "app/models/ControlNet",
        "embeddings": "app/models/embeddings",
        "loras": "app/models/loras",
        "upscale_models": "app/models/upscale_models",
        "vae": "app/models/VAE"
      },
      "peers": [
        "https://github.com/cocktailpeanutlabs/automatic1111.git",
        "https://github.com/cocktailpeanutlabs/fooocus.git"
      ]
    }
  }, {
    "method": "fs.share",
    "params": {
      "drive": {
        "output": "app/output"
      }
    }
  }, {
    "method": "fs.share",
    "params": {
      "venv": "app/env"
    }
  }, {
    "method": "fs.download",
    "params": {
      "url": "https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors",
      "dir": "app/models/Stable-diffusion"
    }
  }, {
    "method": "fs.download",
    "params": {
      "url": "https://huggingface.co/stabilityai/stable-diffusion-xl-refiner-1.0/resolve/main/sd_xl_refiner_1.0.safetensors",
      "dir": "app/models/Stable-diffusion"
    }
  }, {
    "method": "notify",
    "params": {
      "html": "Click the 'Start' tab to get started!"
    }
  }]
}
