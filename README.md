基于minddifufusion 悟空画画模型代码，我们将部分代码进行了修改 

训练好的Lora模型已经放在该项目中

# 训练环境

CUDA 11.6

Mindspore 1.9.0

英伟达A6000显卡

Linux_x86 64位系统

注意：训练和文生图代码默认为“GPU"加速，如需Ascend处理器加速，请在代码中修改。

# Lora训练配置

1.训练时需将图片和数据集从对应文件夹中提取到dataset文件夹中。训练使用的数据在"Robots"、"Cyberpunk"和"Pandas"三个文件夹中。

2.训练前请将train.py第235行的"output/"路径改成output文件夹的绝对路径，否则报错

注意：只能单次训练一个Lora文件，即训练完一种数据的Lora模型，当训练其他数据的Lora模型，需要将dataset中的文件清空并重新加载

# 文生图配置

训练完Lora文件后得到的文件将会自动放在output文件夹中，由于为了方便，已训练的Lora文件放在inference.py同一路径下，可以直接使用。

inference.py使用了三个Lora文件，分别使用"Robots"、"Cyberpunk"和"Pandas"两个文件夹数据训练得到。

输出的图片将会在.../outputs/sample/路径中

# 推理结果

我们最后的推理生成图路径为：picture/成果图.png

有三张图片作为测试图

# 其余文件夹说明

dataset 训练用数据放置位置

Cyberpunk 赛博朋克数据及数据集

Pandas 熊猫数据及数据集

Robots 机器人数据及数据集

tk mindpet大模型低参微调组件库（原名tk）

output 推理输出文件夹

ldm 悟空画画组件库

config 配置文件夹

# Notice

理论上输入同样的提示词，使用相同的随机种子和相同的模型，可以得到一样的图片，但是经过实际测试，多次运行同样的代码和模型，产生的图片也会有一定的差别。建议复现时，可以在inference.py第145行中，将n_iter调大，可以更快得到理想的图片。