# 📝 2021-11-25

- Nginx: 413 – Request Entity Too Large Error and Solution

<br>

## 🖥 Nginx: 413 – Request Entity Too Large Error and Solution

  크기가 2MB인 사진이 업로드가 되지 않았고, 413 Request Entity Too Large error가 떴다. 

  <img width="800" alt="width800" src="https://user-images.githubusercontent.com/59908525/143443590-6efcd9c7-861f-495a-b33a-fdcb5245ba31.PNG">

<br>

<<<<<<< HEAD
## 🖥 Nginx: 413 – Request Entity Too Large Error and Solution

  먼저 nginx의 파일 업로드 크기를 정해야 한다. 설정 하지 않은 경우 1M가 넘을 경우에 에러가 발생할 수 있다고 한다. 
=======
## 🖥 Solution
  
  Nginx 설정을 바꾸었다.
  
  1. sudo -s
>>>>>>> 2e14283aa29a9c1d5cd23df64da6a8721a7c96a7

  그래서 우선 파일 업로드 사이즈를 설정하기 위해서는 먼저 nginx의 설정 파일을 수정했다.

  1. nginx.conf 파일의 경로를 찾는다
  ```
  $ sudo vim /etc/nginx/nginx.conf

  ```

  2. nginx.conf의 http{} 내용 부분에 사진의 max 값을 지정해준다. 이 경우에는 100Mbyte로 설정을 해주었다.
  ```
  http{
      # Set client upload size - 100Mbyte
      client_max_body_size 100M;

      ...
      ..
      ..
      .
  }

  ```

![nginx_reverse_proxy](https://user-images.githubusercontent.com/59908525/145716359-9220f78d-9500-4f30-bb5b-234f66cad909.jpg)


  3. 그 후 저장하고 나온 후, nginx를 재시작합니다
  ```
  sudo nginx -s reload
  ``` 

  4. 아니면 서비스를 재시작한다.
  ``` 
  sudo nginx restart
  ```