# 📝 2021-11-24

- S3 image resizing


## 🖥 1. S3 image resizing 전

```
const upload = multer({
    storage: multerS3({
      s3: s3,
      bucket: process.env.BUCKET,
      // access control list : 접근 permission 어디까지 하냐
      acl: 'public-read-write',
      key: function (req, file, cb) {
        // extension이 png인지, jpg인지
        const extension = path.extname(file.originalname);
        cb(null, Date.now().toString() + extension);
      },
    }),
  });
```
<br>

## 🖥 2. 이미지 resize을 할 때, 이미지의 width를 400으로 두었고, rotate을 했다.

- **속도는 2.11s가 측정되었다.**
<img width="420" alt="width400" src="https://user-images.githubusercontent.com/59908525/143442132-fc8befba-f313-452f-ba77-4a90d93c386e.PNG"  width="500" height="500"/>


```
const upload = multer({
  storage: multerS3({
    s3: s3,
    bucket: process.env.BUCKET,
    contentType: multerS3.AUTO_CONTENT_TYPE,
    shouldTransform: true,
    transforms: [
      {
        id: "resized",
        key: function (req, file, cb) {
          try {
            const fileType = file.mimetype.split("/")[0] != "image";
            if (fileType) {
              // 이미지 타입 아님
              return cb(new Error("Only images are allowed"));
            }
            let ex = file.originalname.split(".");
            cb(
              null,
              "img" +
                Date.now() +
                parseInt(Math.random() * (99 - 10) + 10) +
                "." +
                ex[ex.length - 1]
            );
          } catch {
            return cb(new Error("multer image upload error"));
          }
        },
        transform: (req, file, cb) => {
          cb(null, sharp().resize({ width: 400 }).rotate());
        },
      },
    ],
    acl: "public-read-write",
  }),
});
```

<br>

## 🖥 3. 아직 이미지 업로드 속도가 느려서, 이미지의 width를 300, height를 300으로 설정하였고, rotate을 했다.

- 같은 사진으로 속도 측정 결과, 1832.63ms, 약 1.8초가 걸렸다.
<img width="417" alt="300, 300" src="https://user-images.githubusercontent.com/59908525/143442413-3c845307-3598-4c4f-8e2a-5611923758e6.PNG">

```
const upload = multer({
  storage: multerS3({
    s3: s3,
    bucket: process.env.BUCKET,
    contentType: multerS3.AUTO_CONTENT_TYPE,
    shouldTransform: true,
    transforms: [
      {
        id: "resized",
        key: function (req, file, cb) {
          try {
            const fileType = file.mimetype.split("/")[0] != "image";
            if (fileType) {
              // 이미지 타입 아님
              return cb(new Error("Only images are allowed"));
            }
            let ex = file.originalname.split(".");
            cb(
              null,
              "img" +
                Date.now() +
                parseInt(Math.random() * (99 - 10) + 10) +
                "." +
                ex[ex.length - 1]
            );
          } catch {
            return cb(new Error("multer image upload error"));
          }
        },
        transform: (req, file, cb) => {
          cb(null, sharp().resize({width:300, height:300}).rotate());
        },
      },
    ],
    acl: "public-read-write",
  }),
});
``` 
<br>

## 🖥 4. width:parseInt(size[0]),height:parseInt(size[1]).rotate()으로 사진이 업로드 될 때, resize되도록 설정하였다. 
사실 아직 이 코드의 원리를 잘 이해하지 못해서 더 공부를 한 다음에, TIL에 다시 작성해야겠다. 

- 같은 사진으로 측정 결과, 총 823.7ms가 나왔고, 약 0.8초가 나왔다.
<img width="414" alt="size0size1" src="https://user-images.githubusercontent.com/59908525/143442421-49badc53-64d4-4b8e-b002-2a7af6e60285.PNG">


```
const upload = multer({
  storage: multerS3({
    s3: s3,
    bucket: process.env.BUCKET,
    contentType: multerS3.AUTO_CONTENT_TYPE,
    shouldTransform: true,
    transforms: [
      {
        id: "resized",
        key: function (req, file, cb) {
          try {
            const fileType = file.mimetype.split("/")[0] != "image";
            if (fileType) {
              // 이미지 타입 아님
              return cb(new Error("Only images are allowed"));
            }
            let ex = file.originalname.split(".");
            cb(
              null,
              "img" +
                Date.now() +
                parseInt(Math.random() * (99 - 10) + 10) +
                "." +
                ex[ex.length - 1]
            );
          } catch {
            return cb(new Error("multer image upload error"));
          }
        },
        transform: (req, file, cb) => {
          cb(null, sharp().resize({width:parseInt(size[0]),height:parseInt(size[1])}).rotate());
        },
      },
    ],
    acl: "public-read-write",
  }),
});
``` 
