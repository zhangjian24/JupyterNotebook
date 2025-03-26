FROM nvidia/cuda:12.6.3-base-ubuntu22.04

RUN apt update && apt install -y git-all curl
RUN cd /home && git clone https://github.com/comfyanonymous/ComfyUI
RUN cd /home/ComfyUI && pip install --user xformers!=0.0.18 insightface onnxruntime-gpu diffusers ultralytics -r requirements.txt --extra-index-url https://download.pytorch.org/whl/cu121 --extra-index-url https://download.pytorch.org/whl/cu118 --extra-index-url https://download.pytorch.org/whl/cu117
RUN cd /home/ComfyUI/custom_nodes && git clone https://github.com/ltdrdata/ComfyUI-Manager
RUN cd /home/ComfyUI/custom_nodes/ComfyUI-Manager && pip install --user -r requirements.txt

WORKDIR /home/ComfyUI/

EXPOSE 8188
ENTRYPOINT ["python","main.py"]
HEALTHCHECK --interval=8s --timeout=5s CMD curl -fs http://localhost:8188/ || exit 1
