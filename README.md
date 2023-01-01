# Application of Causal Attention Learning in Industrial Fault Diagnosis



## 实验环境
请按照此要求设置环境。通常，您可能需要运行以下命令：

```shell
conda create -n CAL python=3.8
conda activate CAL
conda install pytorch cudatoolkit=11.6 -c pytorch
conda install opencv scikit-learn networkx pandas tqdm matplotlib seaborn
pip install torch==1.12.0
pip install torch-scatter==2.0.9 -f https://pytorch-geometric.com/whl/torch-1.12.0+cu116.html
pip install torch-sparse==0.6.14 -f https://pytorch-geometric.com/whl/torch-1.12.0+cu116.html
pip install torch-cluster==1.6.0 -f https://pytorch-geometric.com/whl/torch-1.12.0+cu116.html
pip install torch-spline-conv==1.2.1 -f https://pytorch-geometric.com/whl/torch-1.12.0+cu116.html
pip install torch-geometric==2.0.4
```



## 数据集下载

**三相流动设施数据：**克兰菲尔德大学的三相流动设施（TFF）设计用于控制加压系统，并测量水流量、油流量和空气流量。该设施中共有24个传感器，用于测量系统不同关键位置的压力、流速、密度和温度。

**下载地址：**

[A Benchmark Case for Statistical Process Monitoring - Cranfield Multiphase Flow Facility - File Exchange - MATLAB Central (mathworks.com)](https://www.mathworks.com/matlabcentral/fileexchange/50938-a-benchmark-case-for-statistical-process-monitoring-cranfield-multiphase-flow-facility)



## 运行方式
对模型进行训练和测试，执行以下指令：
```shell
python main_real.py --model CausalGAT --dataset TFF
```



## 实验结果

我们将文中给出的模型与其他基线模型进行对比，在三相流动设施数据集上，我们的模型CAL表现出更好的分类性能，测试准确率更高，具体如下表：

|          | GAT  | PKT-MCNN | IAGNN | CAL |
| - | - | - | - | - |
| Accuracy | 0.8692 | 0.8805 | 0.9192 |0.9641|

因此，当我们在该三相流动设施上使用我们提出的模型进行故障诊断，能够更好地识别出故障的发生及其故障类型，尽可能减小对生产造成的损失，最终完成了实验目标。
