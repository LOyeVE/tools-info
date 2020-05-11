# jaeger编译
## jaeger代码路径
```
https://github.com/jaegertracing/jaeger.git
```
## 编译遇到的问题
```
同 Cannot build binaries #1887
GOOS=linux make build-platform-binaries
make[1]: Entering directory `/root/Github/jaeger-master'
CGO_ENABLED=0 installsuffix=cgo go build -trimpath -o ./cmd/agent/agent-linux -ldflags "-X github.com/jaegertracing/jaeger/pkg/version.commitSHA=3b34ac6bcdeb22e09a81c6244bfeed20503a383b -X github.com/jaegertracing/jaeger/pkg/version.latestVersion=v1.17.1 -X github.com/jaegertracing/jaeger/pkg/version.date=2020-05-11T03:10:15Z" ./cmd/agent/main.go
esc -pkg mappings -o plugin/storage/es/mappings/gen_assets.go -ignore assets -prefix plugin/storage/es/mappings plugin/storage/es/mappings
CGO_ENABLED=0 installsuffix=cgo go build -trimpath -o ./cmd/collector/collector-linux -ldflags "-X github.com/jaegertracing/jaeger/pkg/version.commitSHA=3b34ac6bcdeb22e09a81c6244bfeed20503a383b -X github.com/jaegertracing/jaeger/pkg/version.latestVersion=v1.17.1 -X github.com/jaegertracing/jaeger/pkg/version.date=2020-05-11T03:10:17Z" ./cmd/collector/main.go
CGO_ENABLED=0 installsuffix=cgo go build -trimpath -tags ui -o ./cmd/query/query-linux -ldflags "-X github.com/jaegertracing/jaeger/pkg/version.commitSHA=3b34ac6bcdeb22e09a81c6244bfeed20503a383b -X github.com/jaegertracing/jaeger/pkg/version.latestVersion=v1.17.1 -X github.com/jaegertracing/jaeger/pkg/version.date=2020-05-11T03:10:20Z" ./cmd/query/main.go
# github.com/jaegertracing/jaeger/cmd/query/app/ui
cmd/query/app/ui/actual.go:24:19: undefined: assets.FS
make[1]: *** [build-query] Error 2
make[1]: Leaving directory `/root/Github/jaeger-master'
make: *** [build-binaries-linux] Error 2
```
### 解决思路
```
git submodule update --init --recursive
dep ensure
make install-tools
make build-ui
make test
```
#### 环境安装说明
需要安装yarn,gcc,nodejs
```

```







