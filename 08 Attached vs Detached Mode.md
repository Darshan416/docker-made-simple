# 🚢 Mastering Attached vs Detached Modes in Docker 🐳

There are two primary ways to run Docker containers:

## 🔹 Attached Mode:

Your terminal is directly connected to the container’s input/output. This is perfect for debugging, real-time monitoring, or interactively working with the container. For example, running an Nginx container in attached mode lets you see live logs and configuration steps as they happen.

## 🔹 Detached Mode:

Your container runs in the background, freeing your terminal for other tasks. You don’t see logs immediately, but you can fetch them anytime using docker logs. Ideal for running services that should keep running independently — like web servers or background workers.

## Key takeaways:

Use docker run -it for interactive sessions.
Use docker run -d to keep things running in the background.
Combine flags like -d, -p, and --name for powerful container configurations.

Want to see real-time logs from a detached container?
Try docker logs -f `<container-name>`.

## Pro Tip:

If you start a container in attached mode and accidentally close the terminal — it stops! But if it’s in detached mode, it keeps running even if your terminal closes. 🧠
