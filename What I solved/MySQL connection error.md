# 📝 MySQL connection error and Solution

- MySQL connection error and Solution

<br>

## 📌  "Port 3000 is already in use" Error and Solution

<img width="397" alt="port3000isalreadyinuse" src="https://user-images.githubusercontent.com/59908525/145718163-a4bb5b2c-294c-4f0e-824e-96493a767b94.PNG">

<br>

## ⛏️ Solution 1 (Windows)
1. Retrieve the PID that has the given port
```
netstat -ano
```
<img width="522" alt="netstatano" src="https://user-images.githubusercontent.com/59908525/145718165-e6be283d-a02c-4684-bcb2-d1f6afec6b64.PNG">


2. Then kill the PID
```
tskill typeyourPID
```

## ⛏️ Solution 2 (Windows)

This single command line can kill the running port.
```
npx kill-port 3000
```
<img width="313" alt="해결" src="https://user-images.githubusercontent.com/59908525/145718344-039e4df3-3f55-456c-9e9d-30f9b97e22aa.PNG">


## Reference 
https://stackoverflow.com/questions/39322089/node-js-port-3000-already-in-use-but-it-actually-isnt
