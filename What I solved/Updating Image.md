
# 📝 이미지 수정하기

- 드디어 이미지 수정하기 문제 해결

<br>

## 🖥 이미지 수정하기 문제

- 문제: 백앤드에서 multer 모듈을 이용해, S3 bucket에 사진 data를 저장을 한다. post 요청을 통해 사진을 저장하기도 잘 되고, get 요청도 잘 된다. 하지만, 사진을 새로운 것으로 바꾸지 않으면, 사진 수정하기가 안된다. 사진을 새로운 것으로 바꾸지 않으면, 기존에 있던 사진의 url로 저장이 되는 것이 아니라, 사진에 null 값이 온다. 이상했던 것은, postman으로 확인을 했을 땐, 사진을 바꾸지 않아도 잘 수정이 되었고, 수정하기 code도 아시는 멘토님께 확인 결과 문제가 없다고 하셨다.

<br> 

## 📝기존 유저 정보 수정하기 code
<img width="632" alt="version1" src="https://user-images.githubusercontent.com/59908525/142114802-87ad2708-267f-4686-bf70-ee6df17ce812.PNG">


<br>

## ⛏️ 시도한 것들

1. S3에 저장된 URL을 누르면 바로 화면에 보여지는게 아니라, 다운로드가 되었다. 이것도 문제의 원인일까 싶어서, 해결을 했다. 사진 URL을 누르면 다운로드가 되는 형식이 아닌, 사진이 바로 보여지는 것으로 만들었다. 사진 extension(예를 들어, JPG, JPEG, PNG..etc)가 있으면 다운로드가 되어서, 사진이 저장 될 때, 이 extension 없이 S3에 저장되게 설정을 하였더니 해결이 되었다. 하지만 결론적으로는 이미지 수정하기 문제는 해결이 되지 않았다.

<br> 

2. req.body를 console.log를 찍으면, object null prototype이라고 떴다. object를 null로 인식하는 건가 싶었다. json형식으로 보내는게 해결 방법이라고 했다. 밑에 사진을 시도해보라고 stack overflow에 적혀 있었다. 근데 이미 app.js에 있는 코드다. 그래서 object null prototype이라고 뜬다고 이미지 수정하기가 안 되는게 아니었다.

<img width="412" alt="33" src="https://user-images.githubusercontent.com/59908525/142113175-93759cb3-1381-42d3-999e-195569484a31.PNG">


<br>

3. req.body에 이미지를 넣고, req.body 안에 있는 모든 것을 json으로 parse하는 형식이다. 근데 Object object으로 뜨고, url이 보이지 않았다.

<img width="390" alt="json parse" src="https://user-images.githubusercontent.com/59908525/142112892-8117452b-7c30-4e70-ab8c-d5ed670f4a14.PNG">

<br>

## 📌 해결책

- 사진 수정하기 api와 나머지 정보 수정하기 api 따로 만들어 보았다.

- user image 수정하는 기능
<img width="641" alt="user 사진 변경하기" src="https://user-images.githubusercontent.com/59908525/142116469-c53687dd-4554-48af-9f31-0e55186f521a.PNG">

- user 정보만 수정하는 기능
<img width="651" alt="유저 정보만 저장" src="https://user-images.githubusercontent.com/59908525/142116514-ca954aee-e9a2-4c24-8786-444204e2ae50.PNG">


- 잘 해결 되었다! 그래서 dog image, dogsta image 도 이런 방법으로, 이미지 수정하기 따로, 나머지 정보들 수정하기 따로 api를 만들어서 프론트와 통신으로 다시 맞춰보았더니, 이미지 수정하기 문제는 잘 해결되었다.

