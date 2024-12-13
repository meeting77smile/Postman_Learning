## Postman

### 1.Mock servers的建立+json文件的上传

#### 1.1

1. 首先，如图所示，点击左侧导航栏里的Mock servers

2. 点击"+"，新建mock server

3. 在"Request URL"中输入URL地址（即可实现最终生成的总url路径的命名）

4. 在"Response Body"中填写返回结果，即访问该mock url后返回的值

5. 点击"Next"

![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20101124.png?raw=true)



#### 1.2

1. 输入"Mock Server"的名称

2. 可以选择一个环境

3. 点击"Create Mock Server"即可完成最终创建

![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20101942.png?raw=true)



#### 1.3

最终，即可得到创建的Mock servers的url地址

![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20102511.png?raw=true)



#### 1.4 访问该Mock servers

- 复制刚刚得到的url地址，加上"/"+之前自定义url地址，即可得到：
  
  ![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20102630.png?raw=true)

- 若不加上之前自定义的url地址，则回出现错误：
  
  ![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20102617.png?raw=true)

- 所以别忘了加

#### 1.5 应用：利用ajax对其进行请求

- 代码：
  
  ```html
  <!DOCTYPE html>
  <html lang="en">
  
  <head>
      <meta charset="UTF-8">
      <meta name="viewport" content="width=device-width, initial-scale=1.0">
      <title>Document</title>
  </head>
  
  <body>
      <input type="button" value="获取数据" onclick="getData()">
  
      <div id="divl"></div>
  </body>
  <script>
      function getData() {
          //原生的ajax请求在进行操作时主要分为以下三步
          //1.创建XMLHttpRequest
          var xmlHttpRequest = new XMLHttpRequest();
  
          //2.发送异步请求
          xmlHttpRequest.open('GET', 'https://b52b3d24-7b31-40c5-9170-fc36c048391f.mock.pstmn.io/user');
          xmlHttpRequest.send();//发送请求
  
          //3.获取服务响应返回的数据
          xmlHttpRequest.onreadystatechange = function () {
              if (xmlHttpRequest.readyState == 4 && xmlHttpRequest.status == 200) {
                  //4：表示请求已完成且响应已就绪  200：表示请求的状态为'0K'
                  document.getElementById('divl').innerHTML = xmlHttpRequest.responseText;
              }
          }
      }
  </script>
  
  </html>
  ```

- 运行效果：按下“获得数据按钮后，将取得之前设置的返回值（json数据）
  
  ![](https://github.com/meeting77smile/Postman_Learning/blob/main/notes/images/%E5%B1%8F%E5%B9%95%E6%88%AA%E5%9B%BE%202024-12-13%20102656.png?raw=true)


