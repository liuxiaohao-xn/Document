## UniLM
>参考： https://zhuanlan.zhihu.com/p/113380840

>中文UniLM语言模型参考： https://github.com/YunwenTechnology/Unilm
### 模型原理图

<img src="https://pic1.zhimg.com/80/v2-d449d6b43f1497b46b77e438372c69cc_720w.jpg" width="600">


### 模型创新点

让预训练语言模型既可以应用于nlu任务，也可以应用于nlg任务

### 模型思想

1、句子对喂给模型，如 [SOS] S1 [EOS] S2 [EOS]， 其中s2是s1的答案

2、MARK大法：通过不同的掩码方式实现三种不同目标函数的语言模型
    
- 双向语言模型, 如图中间列第一个图, 预测token时可看见s1, s2中所有token;
- 单向语言模型, 如图中间列第二个图, left->right, 预测当前token时只能看到它之前的token;
- seq-to-seq, 如图中间列第三个图, 预测token出现在s1中, 只看见s1中所有的token; 如果预测token出现在s2中, 预测当前token，只能看到s1中全部token和s2中预测token之前的token.
- NSP任务, 和bert一样

3、模型结构和bert-large一致, 由训练好的bert-large模型初始化
