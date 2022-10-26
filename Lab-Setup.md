# Lab-Setup

These are hands-on resources to for the course "Cloud for Partners".

# Slides

https://drive.google.com/drive/folders/1HhkaBI6i15kzqo1UimoHxOqcelQLlrYt?usp=sharing


## List of softwares to be installed
- [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli)
- [Git](https://git-scm.com/downloads)
- [VS Code](https://code.visualstudio.com/)
- [Extentions](https://code.visualstudio.com/docs/editor/extension-marketplace) - c#, Kubernetes, Helm, Docker, Git Lens
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Helm](https://helm.sh/docs/intro/install/) 
- [.Net](https://dotnet.microsoft.com/en-us/download)


# Running a Local Kubernetes Cluster

Kubernetes clusters can have hundreds of nodes in production, but you can run a single-node cluster on your laptop and it works in the same way.

We'll also use [Git](https://git-scm.com) for source control, so you'll need a client on your machine to talk to GitHub.

## Git Client - Mac, Windows or Linux

Git is a free, open source tool for source control:

- [Install Git](https://git-scm.com/downloads)


## Docker Desktop - Mac or Windows

If you're on macOS or Windows 10 Docker Desktop is the easiest way to get Kubernetes:

- [Install Docker Desktop](https://www.docker.com/products/docker-desktop)

The download and install takes a few minutes. When it's done, run the _Docker_ app and you'll see the Docker whale logo in your taskbar (Windows) or menu bar (macOS).

> On Windows 10 the install may need a restart before you get here.

Click _Settings_:

<img width="591" alt="image" src="https://user-images.githubusercontent.com/11691661/195954055-f1491bbf-e0da-4f0e-b9bf-261cf655ebf4.png">

In the settings Windows select _Kubernetes_ from the left menu and click _Enable Kubernetes_: 

<img width="996" alt="image" src="https://user-images.githubusercontent.com/11691661/195953987-0422c4bf-c057-4937-a516-5a92ebb5ff8e.png">

> Docker downloads all the Kubernetes components and sets them up. That can take a few minutes too. When the Docker logo and the Kubernetes logo in the UI are both green, everything is running.

## Check your cluster

You should be able to run this command and get some output about your cluster:

```
kubectl get nodes
```

I'm using Docker Desktop and mine says:

```
NAME             STATUS   ROLES    AGE    VERSION
docker-desktop   Ready    master   5d4h   v1.19.7
```

> Your details may be different - that's fine. If you get errors then we need to look into it, because you'll need your own cluster for every part of the course.


