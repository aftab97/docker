FROM node:14

WORKDIR /app
# . <- refers to working dir (/app)
COPY package.json . 

RUN npm install
# copy everything in this folder to /app dir - 
# this is not needed because is being important folders being = copied with -v /app/node_modules
# HOWEVER it is good to do because it creates snapshots - later can be used for deployment to prod
# can restrict what gets copied with .dockerignore (node_modules (local) or .git, etc...)
COPY . .

# ENV PORT=80
# or you can do --env PORT=80 OR -e PORT=80 or use a .env file with argument --env-file .env
# possible problem change to PORT=8000 you will have to change this to -p 3000:8000
# best practice is to set env variables via docker run -e PORT=8080
# because someone can look inside dockerfile via docker history <image>

EXPOSE 3000

# this is path inside container which will get stored somewhere in my machine (Docker controls where it is stored)
# VOLUME [ "/app/feedback" ]

CMD [ "npm", "start" ]

# to build 
# docker build -t feedback-node .

# to run 
# docker run -p 3000:80 -d --name feedback-app --rm feedback-node:latest
# docker run -p 3000:80 -d --name feedback-app -v feedback:/app/feedback -v "/Users/aftab/Desktop/coding/docker/data-volumes-01-starting-setup:/app" -v /app/node_modules feedback-node:w-volumes
#  -p is for ports
#  -d is detached mode for terminal
#  -rm will remove container when stoppped
#  :ro stop docker from writting into folder

# to stop 
# docker stop feedback-app

# NOTE: because you removed the docker container (--rm) it will lose any files it had stored
# but if you only stop you will still see the files

# to look at logs 
# docker logs feedback-app