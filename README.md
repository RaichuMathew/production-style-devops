# Dockerized Python Application

## Objective
Containerize a Python application and deploy it with custom port mapping.

## Base Image
python:3.10-slim

## Build Image
docker build -t nautilus/python-app .

## Run Container
docker run -d --name pythonapp_nautilus -p 8096:8084 nautilus/python-app

## Port Mapping
Container Port: 8084  
Host Port: 8096  

## Test
curl http://localhost:8096

## Concepts Demonstrated
- Image layering optimization
- Dependency management
- Non-root user security
- Port mapping
- Container networking
