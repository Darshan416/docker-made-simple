# 🔍 **What's the Difference Between ARG and ENV?**

When building Docker images, understanding how to pass and persist data is crucial. Two commonly confused instructions are ARG and ENV. Here's a quick breakdown:

## ⚙️ **ARG (Build-time variable)**

Used only during the image build process.
It cannot be accessed after the image is built.
Useful for passing build-specific values like version numbers, API keys (preferably temporary), or custom flags.

```
ARG VERSION=1.0
RUN echo "Building version $VERSION"
```

## 🛠️ ENV (Runtime environment variable)

Available during build and at runtime.
Persists in the final image and can be used by containers started from it.
Ideal for configuration settings needed during execution.

```
ENV APP_ENV=production
CMD ["node", "server.js"]
```

## 🔄 TL;DR

Use ARG for build-time configs.
Use ENV for runtime configs.

You can also combine them:

```
ARG STAGE=dev
ENV NODE_ENV=$STAGE
```

💡 Mastering these small differences helps make your Dockerfiles cleaner, safer, and more flexible.
