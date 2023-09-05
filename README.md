# chat2db-chatglm-6b-deploy

## 📖 Introduction
This project shows how to deploy chatglm-6b to the free cloud resources or your local machine. And it also shows how to use the chatglm-6b in chat2db client.

## 📦 Prerequisites
| Model | GPU(Inference) | GPU(Finetue) |
| :----: | :----: | :----: |
| ChatGLM-6B-int4 | 6GB | 7GB |
## 📦 Deploy
### 📦 Deploy to the google colab
1. Open the [chatglm-6b-int4-deploy.ipynb](https://colab.research.google.com/drive/1-jKsKISmlMCWTbaV-3HYBWbrTWxNLzOo?usp=sharing) in the google colab. In our case, we can run the model in google colab absolutely free.
2. Run the code of step1 to step6 in the notebook.
3. After the step6, you will get the public demo url for your model such as `https://3cef73d65765afdfea.gradio.live`. Click the url to check if the model is deployed successfully. And you can also experiment with the model as you want. Click stop button to stop the web demo.
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/4bc2c26f-fa57-44be-a336-3e5729a2d104.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">
4. Run the code of step7 to step9 in the notebook.
5. After the step9, you will get the api url for your model such as `https://dfb1-34-87-2-137.ngrok.io`. Run below code in your local machine to check if the model is deployed successfully. 
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/bec200c8-a343-45ff-b9a0-2bd21985da9a.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">
```bash
curl -X POST "your api url" \
     -H 'Content-Type: application/json' \
     -d '{"prompt": "Hello", "history": []}'
```
6. After you get the result, you can copy the url and use it in the chat2db client. Set the url in the client as below:
<img src="https://alidocs.oss-cn-zhangjiakou.aliyuncs.com/res/4j6OJdYA60Y7n3p8/img/ca844185-2744-49e0-ab75-245e19b872d6.png?x-oss-process=image/resize,w_640,m_lfit,limit_1">
7. Now you can chat with the model in the chat2db client. Enjoy it!

* Note: The google colab will disconnect after 12 hours. You can rerun the notebook to get the public demo url and api url again. And also, the network speed of google colab is not very fast. So it may take a long time to download the model and run the model. Please be patient.

### 📦 Deploy to the local machine
* Since the network in google colab is not very fast, we can also deploy the model to our local machine. The script for deploy in your local machine is similar to the script in the google colab. Just follow the steps in [chatglm-6b-int4-deploy.ipynb](https://colab.research.google.com/drive/1-jKsKISmlMCWTbaV-3HYBWbrTWxNLzOo?usp=sharing).
* Note: when you deploy the model in your local machine, you need to change the model path from '/content/chatglm-6b-int4' to the path of your local machine. You need also change the api url in the chat2db client to the url of your local machine.