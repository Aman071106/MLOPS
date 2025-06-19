### converting a app to docker Image

1. Create a `Dockerfile` in your main directory.This file contains the commands for docker configuration for creating a docker image.
2. The lower `baseImage` in any docker image should be of linux kernel/os.
3. Template
```DockerFile
FROM baseImage
COPY
WORKDIR 
RUN 
CMD
```
4. Example
```DockerFile
FROM python:3.8-slim
COPY . /app
WORKDIR /app
RUN pip install --upgrade pip && pip install --no-cache-dir -r requirements.txt
CMD ["python", "app.py"]
```
- from baseimage(should be linux image) that is here a python image from dockerhub.
- copy everythin in current directory to a new directory /app
- WORKDIR set to /app
- Run the installation command
- Run the app

5. In current directory
```bash
docker build -t yourNewImagename(lowercase) .
```
- Here '.' represents the current directory
- Alert ⚠️ `Dockerfile` , not `DockerFile`

6. Check
docker images  
REPOSITORY               TAG       IMAGE ID       CREATED          SIZE
firstimage               latest    816b4bf33900   17 seconds ago   143MB

7. 
docker run -p 5000:5000  firstimage

- Output- We see such logs if we don't run in detached mode otherwise we can see them in dockerdesktop
```bash
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://172.17.0.3:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 799-954-373
```
- Here first url will not work as it is container url,
the second one will work, if our app uses 0.0.0.0 then can be accessed through local ip also

- Note ⚠️, if we run
docker run  -p 8000:5001  firstimage
```bash
 * Serving Flask app 'app'
 * Debug mode: on
WARNING: This is a development server. Do not use it in a production deployment. Use a production WSGI server instead.
 * Running on all addresses (0.0.0.0)
 * Running on http://127.0.0.1:5000
 * Running on http://172.17.0.3:5000
Press CTRL+C to quit
 * Restarting with stat
 * Debugger is active!
 * Debugger PIN: 998-231-809
```
* Running on http://127.0.0.1:5000 
* Running on http://172.17.0.3:5000
These points to what port is provided in app , not the ports in command. We can see them in dockerhub and also those are correct ports not  these.
