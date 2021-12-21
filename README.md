# 基于 pprof,fgprof 的 Golang 程序连续分析

[![Go Report Card](https://goreportcard.com/badge/github.com/xyctruth/profiler)](https://goreportcard.com/report/github.com/xyctruth/profiler)
[![codecov](https://codecov.io/gh/xyctruth/profiler/branch/master/graph/badge.svg?token=YWNYJK9KQW)](https://codecov.io/gh/xyctruth/profiler)
[![Build status](https://img.shields.io/github/workflow/status/xyctruth/profiler/server/master)](https://github.com/xyctruth/profiler/actions/workflows/server.yml)

## [Demo](https://profiling.jia-huang.com)

![profiler](https://xtruth.oss-cn-shenzhen.aliyuncs.com/profiler_1.png)
 
### 点击 point 跳转 pprof web
![pprof](https://xtruth.oss-cn-shenzhen.aliyuncs.com/6.png)


## Quick Start

需要被收集分析的golang程序,需要提供 `net/http/pprof` 端点，并配置在 `./collector.yaml` 配置文件中

程序会 watch `collector.yaml` 配置文件变化, 实时加载变化的配置

### 本地启动
```bash
     # run server :8080
    go run server/main.go 
     # run ui :80
    cd ui && npm install --registry=https://registry.npm.taobao.org  &&  npm run dev --base_api_url=http://localhost:8080 
```

### In Docker
```bash
    # 简单启动
    docker run -d -p 80:80 --name profiler xyctruth/profiler:latest

    # 挂载目录启动
    mkdir -vp ~/profiler/config/
    cp ./collector.yaml ~/profiler/config/
    docker run -d -p 80:80 -v ~/profiler/data/:/profiler/data/ -v  ~/profiler/config/:/profiler/config/ --name profiler xyctruth/profiler:latest
```
