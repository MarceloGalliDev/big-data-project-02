### Dockerfile Struct
- The Dockerfile is built layer by layer.
- OCI is the same thing as a image docker.
- Registries is the organizations that store the docker images.
-  

> Example:
> ```
> FROM Python
> RUN pip install django
> WORKDIR /app
> COPY . .
> CMD python app.py
> ```

> `FROM Python`= This line tells Docker to use the Python image as the base image for our container.

> `RUN pip install django`= This line installs the Django framework on the container.

> `WORKDIR /app`= This line sets the working directory of the container to /app.

> `COPY . .`= This line copies all the files in the current directory to the /app directory in the container.

> `CMD python app.py`= This line sets the default command that will be executed when the container starts.

### Docker Commands

> ```
> docker run -d -p 8800:80 httpd
> ```

> `-d` for execute in background

> `-p` for open an port and published