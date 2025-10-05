# 🚀 Dockerfile Essentials

In MLOps, reproducibility and portability are non-negotiable — whether you're training models on GPU clusters or deploying them as APIs. Your Dockerfile is the single source of truth for your ML environment.

## **Here’s how we structure it:**

🧬 **FROM** – Choose a lightweight yet ML-friendly base (e.g., python:3.9-slim, nvidia/cuda for GPU).

🏷️ **LABEL** – Add metadata (project, version, maintainer) for traceability and image management.

🌐 **ENV** – Set environment variables like MODEL_DIR, ENV=production, or TRACKING_URI.

👤 **USER** – Run processes as a non-root user to reduce attack surface.

📁 **COPY** – Copy code, models, and config files from the build context.

🔧**ARG** – Define build-time variables (e.g., ARG PYTHON_VERSION=3.10). Great for parameterizing the build without hardcoding.

⚙️ **RUN** – Install dependencies (RUN pip install --no-cache-dir -r requirements.txt). Minimize image size by combining commands.

🧭 **WORKDIR** – Define a clean working directory (e.g., /app). Keeps builds organized.

📌 **CMD** – The default command (e.g., uvicorn main:app or python[predict.py](http://predict.py/)). Only the last CMD runs.

💡 **Pro Tip**: Use multi-stage builds to separate training and inference environments — and keep production images minimal.

Consistency between local, dev, and production = fewer bugs, faster iterations, and reliable deployments.
