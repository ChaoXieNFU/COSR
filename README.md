# COSR
Paper is under peer view.
The code is built on [EDSR (Pytorch)](https://github.com/sanghyun-son/EDSR-PyTorch). We thank the authors for sharing the codes.

## Abstract
Recently, deep learning techniques have been deeply studied and widely applied to single image super-resolution (SR). Increasingly, deeper and wider convolution neural networks (CNNs) are customized for SR, and many favorable and beneficial mechanisms are introduced to make further progress. Among them, channel attention has drawn the majority of attention due to its great boost in the presentational power of CNNs. However, the original channel attention neglects the critical importance of positional information, thus imposing performance limitations. In this paper, we explore a novel perspective, namely the coor-dinate attention mechanism, to alleviate the aforementioned problem, and accordingly result in an enhanced SR performance. Specifically, we propose a deep residual coordinate attention SR network (COSR), which mainly incorporated the presented co-ordinate attention blocks into a deep nested residual structure. The coordinate attention captures the positional information by computing the average value vector from the two spatial directions respectively, thus aggregating the features in different coor-dinates. The nested residual blocks pass low-frequency information from top to end through the skip-connection lines, allowing convolution filters to concentrate more on high-frequency textures and edges and therefore reducing the difficulty of recon-struction. Extensive experiments demonstrate that our proposed COSR achieves better performance and exceeds many state-of-the-art SR methods in terms of both quantitative metrics and visual quality.

## Train

x2: 
```
python main.py --template COSR --save COSR_BIX2_G10R20P48 --scale 2 --reset --save_results --patch_size 96 --dir_data C:\DIV2K\ --data_test Set5 --epochs 1000
```
x3:
```
python main.py --template COSR --save COSR_BIX3_G10R20P48 --scale 3 --reset --save_results --patch_size 144 --dir_data C:\DIV2K\ --data_test Set5 --epochs 1000
```
x4:
```
python main.py --template COSR --scale 4 --save COSR_BIX4_G10R20P48 --save_results --patch_size 192 --dir_data C:\DIV2K\ --data_test Set5 --pre_train ../experiment/COSR_BIX4_G10R20P48/model/model_latest.pt
```

## Test

x2:
```
python main.py --template COSR --data_test Set5+Set14+B100+Urban100+Manga109 --dir_data C:\ --scale 2 --pre_train ..\experiment\COSR_BIX2_G10R20P48\model\model_best.pt --test_only --save_results --self_ensemble
```
x3:
```
python main.py --template COSR --data_test Set5+Set14+B100+Urban100+Manga109 --dir_data C:\ --scale 3 --pre_train ..\experiment\COSR_BIX3_G10R20P48\model\model_best.pt --test_only --save_results --self_ensemble
```
x4:
```
python main.py --template COSR --data_test Set5+Set14+B100+Urban100+Manga109 --dir_data C:\ --scale 4 --pre_train ..\experiment\COSR_BIX4_G10R20P48\model\model_best.pt --test_only --save_results --self_ensemble
```
