# 為了上傳至 docker hub 建立的 fork

## 後端 (backend)
### Build 流程
```shell=
$ cd backend
$ DATE=$(date +%Y%m%d)
$ docker build -t screenshot-to-code-backend:$DATE .
$ docker push screenshot-to-code-backend:$DATE
```
### 執行
`docker run --rm -it screenshot-to-code-backend:$DATE poetry run uvicorn main:app --host 0.0.0.0 --port 7001`


### 環境變數
`OPENAI_API_KEY` => api key


## 前端 (frontend)
### Build 流程
```shell=
$ cd frontend
$ DATE=$(date +%Y%m%d)
$ docker build -t screenshot-to-code-frontend:$DATE .
$ docker push screenshot-to-code-frontend:$DATE
```
### 執行
`docker run --rm -it screenshot-to-code-frontend:$DATE`

### 環境變數
`VITE_IS_DEPLOYED` => `true`
`WS_BACKEND_URL` => `ws://127.0.0.1:7001`
`VITE_HTTP_BACKEND_URL` => `http://127.0.0.1:7001`