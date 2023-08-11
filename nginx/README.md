# Introduction
This document describes the steps to create a NGINX docker image with your won HTML files added to the  image.

# Steps
1. Create a directory named `nginx`. If you create a directory with a different name, 
    you need to replace the `nginx` directory name in the following steps with yours.
2. Dopcy the `Dockerfile` and `hello.html` files into the `nginx` directory.
3. Use the `cd <path-to-nginx-dir>` command to make the `nginx` directory as your working directory.
4. Execute the following command to build a new image:  
    ```
    docker build -t mynginx:1.0 .
    ```

    By default the `docker build` command will look for a Dockerfile in the current directory because you have a dot at the last argument to the command and it will start building your image using the instructions in 
    the `Dockerfile`. If your file name 

    Other forms of using the `docker build` command are as follows. 

    ```
    docker build -f /path/to/Dockerfile -t image-name .

    docker build -f /myapp/Dockerfile.prod -t myapp-image /myapp
    ```

    Here, the last argument is the build context directory such as `.` and `/myapp`

    Note that there is a `.` (a dot) at the end of teh command, which means the current directory.
5. Verify that your image is stored locally:  
    ```
    docker image ls
    ```
6. Run your docker image:  
   ```
   docker run -d --rm -p 8080:80  mynginx:1.0
   ```
7. Verify that you can access the hello.html webpage:  
   ```
   curl http://localhost:8080/hello.html
   ```