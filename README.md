# NIfTI_20140122
matlab读取nii所需要的的工具包

使用代码
```matlab
close all;
clear all;
clc;
nii = load_nii( '20191014_200201boldkangfu9ZENGZHIs008a1001.nii' );  % 装载.nii数据
img = nii.img;  % 因为这个文件有img和head二个部分，其中img部分是图像数据
save image.mat img  % 将数据变成mat格式
load 'image.mat'  % 加载数据
[n1, n2, n3] = size(img);   % 获取.nii文件的三个维度，一般1、2维是图像维度，第三维是切片
% imshow(img(:,:,100),[]);  这个是正常显示第100个切片的图像
for i = 1:n3   % 开始切片数据轮寻
    figure(i)   % 开始显示图片
    ti = imshow(img(:,:,i),[]);  % 显示每一张切片图像
    pause(0.1);  % 防止显示过快看不见，简单延时
end

```
