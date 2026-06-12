# 3DGS, why not pinhole camera model?

## Removal of NDC-space calculation from 3DGS custom CUDA Kernel

Overall Requirements:
- CUDA nvcc, no caso 12.4
- nvcc --version # ... Cuda compilation tools, release 12.4, V12.4.131

Force diff-gaussian-rasterization-pinhole reinstall:

```shell
conda env create -f environment.yml
conda activate gs
pip install ./submodules/diff-gaussian-rasterization --force-reinstall 
pip install ./submodules/diff-gaussian-rasterization-pinhole --force-reinstall 
pip install ./submodules/diff-gaussian-rasterization-pinhole-v2 --force-reinstall 
pip install ./submodules/simple-knn --force-reinstall 
pip install ./submodules/fused-ssim --force-reinstall 

# Be aware if using nvcc 12.5
# First use pythorch 12.6 to ensure compilation of above CUDA kernels:
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu126
# But for trainig go for updated pytorch version
pip3 uninstall torch torchvision torchaudio
pip3 install torch torchvision torchaudio --index-url https://download.pytorch.org/whl/cu128
```

Check import:

```shell
python -c "from diff_gaussian_rasterization_pinhole_v2 import GaussianRasterizationSettings, GaussianRasterizer"
```

Usage: 

```shell
python train.py -s ../data_path --use_pinhole
```

<!-- 
git init
git remote add 3dgs https://github.com/HumbertoDiego/extended-3dgs
git pull 3dgs main
# Do and push changes:
git add * ; git commit -m "run final"; git push -u 3dgs main
#Pull changes
git pull origin main 
 -->
