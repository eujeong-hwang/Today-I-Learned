# ๐ 2021-11-25

- Nginx: 413 โ Request Entity Too Large Error and Solution

<br>

## ๐ฅ Nginx: 413 โ Request Entity Too Large Error and Solution

  ํฌ๊ธฐ๊ฐ 2MB์ธ ์ฌ์ง์ด ์๋ก๋๊ฐ ๋์ง ์์๊ณ , 413 Request Entity Too Large error๊ฐ ๋ด๋ค. 

  <img width="800" alt="width800" src="https://user-images.githubusercontent.com/59908525/143443590-6efcd9c7-861f-495a-b33a-fdcb5245ba31.PNG">

<br>

## ๐ Nginx: 413 โ Request Entity Too Large Error and Solution

  ๋จผ์  nginx์ ํ์ผ ์๋ก๋ ํฌ๊ธฐ๋ฅผ ์ ํด์ผ ํ๋ค. ์ค์  ํ์ง ์์ ๊ฒฝ์ฐ 1M๊ฐ ๋์ ๊ฒฝ์ฐ์ ์๋ฌ๊ฐ ๋ฐ์ํ  ์ ์๋ค๊ณ  ํ๋ค. 
  
<br>

## โ๏ธ Solution

  1. ์ฐ์  ํ์ผ ์๋ก๋ ์ฌ์ด์ฆ๋ฅผ ์ค์ ํ๊ธฐ ์ํด์๋ ๋จผ์  nginx์ ์ค์  ํ์ผ์ ์์ ํ๋ค. nginx.conf ํ์ผ์ ๊ฒฝ๋ก๋ฅผ ์ฐพ๋๋ค
  ```
  $ sudo vim /etc/nginx/nginx.conf

  ```

  2. nginx.conf์ http{} ๋ด์ฉ ๋ถ๋ถ์ ์ฌ์ง์ max ๊ฐ์ ์ง์ ํด์ค๋ค. ์ด ๊ฒฝ์ฐ์๋ 100Mbyte๋ก ์ค์ ์ ํด์ฃผ์๋ค.
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


  3. ๊ทธ ํ ์ ์ฅํ๊ณ  ๋์จ ํ, nginx๋ฅผ ์ฌ์์ํฉ๋๋ค
  ```
  sudo nginx -s reload
  ``` 

  4. ์๋๋ฉด ์๋น์ค๋ฅผ ์ฌ์์ํ๋ค.
  ``` 
  sudo nginx restart
  ```
