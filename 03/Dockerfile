# ① ビルドステージ（コンパイルなど開発用ツールが必要）
FROM golang:1.24-alpine3.22 AS builder

WORKDIR /
COPY main.go .
RUN go build main.go

# ② 実行ステージ（成果物だけを含む超軽量イメージ）
FROM alpine:3.22

# 前のステージから必要なファイルだけコピーしてる
COPY --from=builder /main /
CMD ["/main"]