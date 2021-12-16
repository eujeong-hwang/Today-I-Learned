# 📝Cannot install Sharp Module on ubuntu

- Sharp module installation problem and solution

<br>

## ⛏️ Solution
1. Check the node module version
```
node -v
```

2. Update the node module version that supports the version of the sharp module you've installed

    1. If you need to run multiple versions of Node.js on your machine e.g. if you have an older project that targets a specific version on AWS Lambda, you can use NVM.
    
    ```
    curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.0/install.sh | bash
    ```
    2. Install the version of node.js you need
    ```
    nvm install v14.17.6
    ```