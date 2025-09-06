#Build Stage
FROM python:3.13.7-alpine3.22 AS builder

#Adding Labels
LABEL name="PYTHON API" \
    description="This is used as backend API"

#Setup App Directory
WORKDIR /app

#Copy Requirements
COPY requirements.txt .

#Copy Source Code
COPY . .

#Install Packages/Dependencies
RUN pip3 install -r requirements.txt

#Production Stage
FROM python:3.13.7-alpine3.22

#Setup App Directory
WORKDIR /app

#Copy Files from Builder Stage
COPY --from=builder /usr/local/lib/python3.13/site-packages /usr/local/lib/python3.13/site-packages
COPY --from=builder /app ./

#Expose Port
EXPOSE 3001

#Set User
USER nobody

#run Application
CMD [ "python", "index.py"]
