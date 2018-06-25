## 多阶段构建
* ```
  #build stage
  FROM daxiang6506/tf-demo AS builder
  WORKDIR /go/src/app
  COPY . .
  RUN go install 

  #final stage
  FROM daxiang6506/tf-demo
  WORKDIR /app
  COPY --from=builder /go/bin/app /app/app
  COPY --from=builder /go/src/app /app/
  ENTRYPOINT ./app
  LABEL Name=tensorflow-demo Version=0.0.1
  EXPOSE 1323
  ```