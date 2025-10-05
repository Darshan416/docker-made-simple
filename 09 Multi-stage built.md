# 🚢 Level up your Docker builds with Multi-Stage!

If you’ve ever built a Docker image and ended up with something huge, packed with compilers, temporary files, and build tools you don’t even need in production… you’re not alone.
That’s where Docker Multi-Stage Builds come to the rescue. 🛟

## ✅ What is it?

Multi-Stage Builds let you define multiple FROM statements in your Dockerfile — each one a stage.
You can build your app in one stage (with all the tools you need), then copy only the final artifacts into a much slimmer base image in the final stage.

## ✨ Why use it?

Drastically reduces image size 📉
Eliminates unnecessary dependencies in production
Makes builds more secure and maintainable

💡 Bonus: Use --target for intermediate stages!

Sometimes you want to build just one stage (like for testing or debugging before going all the way).
With --target, you can stop at any named stage:

```
docker build --target builder -t myapp:build .
```

And in your Dockerfile:

# Stage 1: Build

```
FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
RUN go build -o myapp
```

# Stage 2: Run

```
FROM alpine:3.20 AS runner
COPY --from=builder /app/myapp /usr/local/bin/
CMD ["myapp"]
```

✅ The command above builds only the builder stage and tags it as myapp:build.

## ⚡ TL;DR:

Multi-Stage Builds → 🪶 smaller, secure images
--target → 🎯 build only what you need (debug/test stages)
