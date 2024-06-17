# ComfyUI-SD3-Medium-CN-Diffusers（WIP）
## ZHO-Prodogape Version

- Since the two orginal forks:
```
  https://github.com/ZHO-ZHO-ZHO/ComfyUI-SD3-Medium-CN-Diffusers
  https://github.com/instantX-research/diffusers_sd3_control
```
are not stable, I forked these two and debugged them until they have worked properly.

- Frankly, the controlnet model and the ComfyUI custom node are not perfect, and maybe I'll develop these codes to make them better.

- Please follow the instruction below.
 
- This repo will install a separatly different version of "diffusers" called "diffusers_sd3_control", which will not destroy your original environment.

### Install

1. git clone this repo
    
```
cd ComfyUI/custom_nodes/

git clone https://github.com/prodogape/ComfyUI-SD3-Medium-CN-Diffusers.git

cd ComfyUI-SD3-Medium-CN-Diffusers
```

2. install sd3 models and controlnet models

```
python  # enter python cmd
>>> from huggingface_hub import login
>>> login()
# Enter your access tokens
>>> from huggingface_hub import snapshot_download
>>> snapshot_download(repo_id="stabilityai/stable-diffusion-3-medium-diffusers")
# Start downloading SD3 models
>>> snapshot_download(repo_id="InstantX/SD3-Controlnet-Canny")
# Start downloading Controlnet models of Canny trained by InstantX
# You can also change "Canny" with "Pose", "Tile"
```

3. modify "model_index.json" of sd3

Please check the "model_index.json" in this repo and replace the contents of the "model_index.json" under 
```
 `~/.cache/huggingface/hub/models--stabilityai--stable-diffusion-3-medium-diffusers/snapshots/???/
```
with it.


4. install "diffusers_sd3_control"
    
```
pip install -r requirements.txt
```
or
```
git clone https://github.com/prodogape/diffusers_sd3_control.git

cd diffusers_sd3_control

pip install -e .
```



---
### README in origin repo:

![screenshot-20240616-034804](https://github.com/ZHO-ZHO-ZHO/ComfyUI-SD3-Medium-CN-Diffusers/assets/140084057/a09efa7c-6df0-464d-a7bc-19c3af913a67)


ComfyUI SD3-Medium ControlNet（Diffusers）


已初步能用，但不推荐本地使用（会自动下模型，会有 diffusers 的版本冲突，仅推荐 colab 云上用），原项目 InstantX/SD3-Controlnet- 的代码有问题，自己踩了3个坑，然后还参考了 [kijai](https://github.com/kijai) 的[代码](https://github.com/kijai/ComfyUI-DiffusersSD3Wrapper) 才发现需要 controlnet_start_step 和 controlnet_end_step 这两个参数才能起作用


另外需要手动装这个版本的 diffusers：

git clone -b sd3_control https://github.com/instantX-research/diffusers_sd3_control.git

cd diffusers_sd3_control（原项目代码这里有问题，这是改好的）

pip install -e .
