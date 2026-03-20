# Media Processing & Tools

## Audio

- **Audio System**: PipeWire (primary), with PulseAudio compatibility layer
- **Microphone**: Blue Yeti USB microphone
- **Audio Recording**: Local Whisper instance for transcription
- **Common Tools**: ffmpeg, sox, audacity for audio processing

## Video & Image Processing

- **Video Editing**:
  - DaVinci Resolve (CUDA-accelerated)
  - ffmpeg for command-line processing and automation
  - Programmatic video editing workflows via Python scripts
- **Image Processing**:
  - GIMP and ImageMagick available
  - Upscaling via Real-ESRGAN (CUDA)

## AI/ML Tools

- **Ollama**: Running locally with RTX 4090
  - Models: llama3.1:70b, codellama:34b, mistral-nemo
  - API at localhost:11434
- **ComfyUI**: Located at `~/opt/ComfyUI/`
  - CUDA-accelerated with RTX 4090
  - Start script: `~/bin/comfyui-start.sh`
- **Stable Diffusion**: Via ComfyUI workflows
- **CUDA Configuration**:
  - CUDA 12.4, cuDNN 8.9
  - CUDA_HOME=/usr/local/cuda

## Local LLMs

- **Ollama**: Primary local inference (see above)
- **llama.cpp**: Available for custom quantizations
- **Preference**: Cloud LLMs via OpenRouter for most tasks, local for privacy-sensitive or high-volume work
