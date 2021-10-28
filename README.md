# 医疗实体及关系识别挑战赛    
## 队名：五叶草
## 运行环境
1. python==3.7.11
2. torch==1.9.0
3. transformers==4.11.3
4. pytorch-lightning==1.4.7
5. tqdm==4.62.3
6. numpy==1.21.0
7. scikit-learn==0.24.2

## 复现流程
1. 原始数据放在`data`文件夹；
2. 下载`chinese-roberta-wwm-ext-large`模型，已发送到邮箱，与开源的有些许差别，`vocab.txt`添加了一些专业的词汇，替换了`[unused1]-[unused36]`；
3. 需要GPU(v100 32G)环境，训练ner模型，大概需要3小时。本地文件夹下运行`global_pointer.py`，将生成数据`data/labels.json`、`data/train.json`、`data/testB_ner.txt`、
   五折交叉的模型`global_pointer_model_1`、`global_pointer_model_2`、`global_pointer_model_3`、`global_pointer_model_4`、`global_pointer_model_5`；
4. 需要GPU(v100 32G)环境，训练relation模型，大概需要12小时。本地文件夹下运行`relation.py`，将生成数据`data_relation/train.json`、`data_relation/submit_B.txt`、
   五折交叉的模型`relation_model_1`、`relation_model_2`、`relation_model_3`、`relation_model_4`、`relation_model_5`；
5. 第4步生成的`data_relation/submit_B.txt`为最终的结果；

## Tips
1. 已经设置seed，按理说可以完全复现；