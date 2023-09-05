# chat2db-chatglm-6b部署

语言：中文  | [English](README.md)

## 📖 简介
这个工程介绍了如何在免费的云资源上部署独立的ChatGLM-6B大模型，并将大模型应用到Chat2DB客户端中。

！！！请注意，为了在消费级显存上也能部署大模型，本教程部署的是ChatGLM-6B的4bit量化模型，模型准确性会有所下降，仅供大家实验参考，切勿迁怒于模型或产品。

## 📦 硬件要求
|       模型        | 最低GPU显存(推理) | 最低GPU显存(高效参数微调) |
|:---------------:|:-----------:|:---------------:|
| ChatGLM-6B-int4 |     6GB     |       7GB       |
## 📦 部署
### 📦 在 google colab 中部署
1. Google colab 每天有免费12小时的使用机会，如果对Google colab不熟悉，可以简单百度一下教程，非常简单。打开 [chatglm-6b-int4-deploy.ipynb](https://colab.research.google.com/drive/1-jKsKISmlMCWTbaV-3HYBWbrTWxNLzOo?usp=sharing). 拷贝一份副本到你自己的Google colab账号中。
2. 依次执行步骤1到步骤6的代码，一定要记得将步骤6中的web_demo.py文件换成本工程中的web_demo.py文件。
3. 执行步骤6之后你将得到一个类似下图中的URL `https://3cef73d65765afdfea.gradio.live`. 点击URL之后即可开始demo体验了，第一轮对话初始化耗时较长，后续对话会相对快一点，点击Google colab中的stop按钮停止demo体验。
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/4bc2c26f-fa57-44be-a336-3e5729a2d104.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">
4. 执行步骤7到步骤9的代码，一定要记得将步骤9中的api.py文件换成本工程中的api.py文件。
5. 你将得到一个api url，类似于`https://dfb1-34-87-2-137.ngrok.io`。在本地机器上运行下面的代码，检查模型是否部署成功。
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/bec200c8-a343-45ff-b9a0-2bd21985da9a.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">
```bash
curl -X POST "你的api地址" \
     -H 'Content-Type: application/json' \
     -d '{"prompt": "Hello", "history": []}'
```
6. 执行以上命令可以正常拿到结果之后，将api url复制到chat2db客户端中，即可开始使用模型生成SQL了。参考下图进行配置
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/ca844185-2744-49e0-ab75-245e19b872d6.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">

* 注意: 因为我们是在Google colab上部署的模型，所以网络有可能比较慢，模型下载和运行的时间可能会比较长，请耐心等待。

### 📦 在本地机器上部署模型
* 如果觉得在云资源上部署模型体验不够丝滑，你也可以在你的本地机器上部署，部署步骤和在Google colab上的部署步骤是一样的。请参考 [chatglm-6b-int4-deploy.ipynb](https://colab.research.google.com/drive/1-jKsKISmlMCWTbaV-3HYBWbrTWxNLzOo?usp=sharing) 中的代码。
* 注意: 在本地部署的时候记得将本工程中的web_demo.py文件和api.py文件中的/content/chatglm-6b-int4路径换成你本地机器上的chatglm-6b-int4模型路径。另外，记得将chat2db客户端中的api url换成你本地机器上的api url。