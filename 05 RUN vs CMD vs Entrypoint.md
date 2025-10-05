# 🐳 RUN vs CMD vs ENTRYPOINT – What’s the Real Difference?

Let’s break it down. 👇

## 🔨 RUN — Executed During Image Build

✅ RUN is used to install dependencies, configure software, or prepare your environment while building the image.
✅ The result of this command is saved in the image layer.
❌ It does not run when the container starts.

**🔧 Example:**
RUN apt-get update && apt-get install -y curl

**Use it for:**
Installing system packages
Compiling source code
Creating necessary directories or files
Any setup that should be “baked into” the image

## 🚀 CMD — Executed When Container Starts

✅ CMD defines the default command that gets executed when a container starts.
✅ Can be overridden at runtime:
docker run myimage python[other_script.py](http://other_script.py/)

🎯 **Example:**
CMD ["python", "[app.py](http://app.py/)"]

**Use it to:**
Start your web server
Launch your Python or Node app
Set the default behavior if no command is specified at docker run

## ⚓ ENTRYPOINT — Also Executed When Container Starts

✅ ENTRYPOINT defines the main command that always runs in the container.
✅ You can still pass arguments at runtime to complement it.
✅ Unlike CMD, it’s harder to override the executable itself (unless you use entrypoint explicitly).

**🎯 Example:**
ENTRYPOINT ["nginx"]
CMD ["-g", "daemon off;"]
Here, nginx is fixed, but you can override the flags.

**Use it to:**
Enforce a specific executable
Build images for a single-purpose container

🧠 **Pro Tip:**
✅ Use RUN for building
✅ Use ENTRYPOINT + CMD for runtime: ENTRYPOINT defines what, CMD defines how.
🕤 RUN builds it. ENTRYPOINT runs it. CMD customizes it.
