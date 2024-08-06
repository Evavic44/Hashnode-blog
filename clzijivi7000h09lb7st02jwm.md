---
title: "How to run Localhost on your Mobile Device using ngrok"
seoTitle: "How to run Localhost on your Mobile Device using Ngrok"
seoDescription: "Learn how to run and test your web applications changes without deploying using Ngrok—a globally distributed reverse proxy that creates secure tunnels to yo"
datePublished: Tue Aug 06 2024 14:53:32 GMT+0000 (Coordinated Universal Time)
cuid: clzijivi7000h09lb7st02jwm
slug: how-to-run-localhost-on-your-mobile-device-using-ngrok
canonical: https://victoreke.com/blog/run-localhost-on-mobile-device-using-ngrok
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1722955216871/8bcb3f11-05c0-4d19-a5cc-1b61adf68a36.png
tags: hosting, apis, ci-cd

---

Accessing your localhost environment on a mobile device is something every web developer have tried or hoped was readily available. This capability can be a game-changer for testing the responsiveness of a site or addressing mobile-specific issues.

In this article, you'll learn how to run your localhost environment directly on your mobile device and even share it with others using [ngrok](https://ngrok.com).

## The Traditional Approach

Before ngrok, in other to run a localhost environment in a mobile device, you would first connect both your PC (where the local server is running) and your mobile device to the same network, and then attach the port number of your local app to your IP address, like **192.168.1.2:3000**. Although this approach may work, it is sometimes unreliable and prone to connectivity issues, which makes it less efficient for consistent testing.

Additionally, you would not be able to share your localhost environment with others, as they need to be on the same local network. This is where ngrok comes in.

> **Disclaimer:** I am in no way associated with ngrok. I am sharing this because it has been helpful in my development process and I believe it may be helpful to other developers.

## Using ngrok

ngrok is a a globally distributed reverse proxy that secures, protects and accelerates your applications and network services, no matter where you run them. It allows you to test your app development, create customizable domains, test webhooks and more.

ngrok operates over the internet, meaning you can share your localhost server with others for testing. Unlike traditional hosting, ngrok is much easier. With a single command, you can serve multiple localhost servers without leaving your terminal.

Enough said! Here are the steps to run your localhost server on mobile:

### Step 1. Create an ngrok Account

To deploy your localhost online, you need to generate an authtoken on ngrok. Visit [ngrok.com](http://ngrok.com) to create a new account.

### Step 2. Configure ngrok on your Machine

ngrok can run in various environments, machines, and SDKs. To configure it for your specific machine, follow their Setup and Installation guide. Installing ngrok is as easy as running the command below for your specific machine below:

```bash
# MacOS
brew install ngrok/ngrok/ngrok

# Windows
choco install ngrok

# Linux
curl -s https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
	| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
	&& echo "deb https://ngrok-agent.s3.amazonaws.com buster main" \
	| sudo tee /etc/apt/sources.list.d/ngrok.list \
	&& sudo apt update \
	&& sudo apt install ngrok
```

> This command requires specific package managers installed on your machine (Homebrew for MacOS, and chocolatey for windows).

Alternatively, you can download the ngrok file onto your machine by clicking the download tab on the ngrok dashboard.

![Download ngrok exe file for windows](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954716955/2b59e4de-b4ad-47dc-b2de-a5d55b93e9b0.png align="center")

### Save ngrok Executable File Path to Environment Variables (Windows only)

The ngrok executable file is the entrance by which the ngrok interface is accessible in your terminal. To always have this interface available in your terminal, it's important you store the file path in your environment variables.

Since you'll be storing the path in the environment variables, it's best to create a permanent folder and moved the executable file into this folder to be provided as the path. Here are the steps:

1. Create a folder on your PC named `ngrok`, preferably inside your `C:\Users\` directory. Copy the folder path by clicking on the search bar where the path is listed.
    

![ngrok.exe file inside the C:\Users\USER\ngrok directory](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954794511/59553de8-adb8-4e48-b2df-d34f6780aaea.png align="left")

2. Open a Run box by holding down `Win + R` on your keyboard, type `sysdm.cpl`, and hit OK.
    

![Open System Device Manager](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954856768/2efa1f6a-bf19-4b54-a175-a5df23b78f64.png align="left")

3. In the System Properties panel, navigate to the "Advanced" tab and click the Environment Variables button.
    

![Advanced tab of System Properties panel](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954901355/d55a49a6-4645-48bc-99ed-d17a50cf6ee9.png align="left")

4. In the Environment Variables tab, double-click on the Path line to edit it. Click the "New" button and paste the ngrok path you copied earlier.
    

![ngrok folder location added to environment variable path](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954930189/7be9b81d-aeb3-4caa-a071-ea7c66f0c589.png align="left")

5. Save this new variable by clicking OK on the screens.
    

To check if you configured the path correctly, open a terminal and type `ngrok -v` and hit Enter. If successful, you should see the version installed on your machine.

![command prompt showing ngrok versions 3.13.0](https://cdn.hashnode.com/res/hashnode/image/upload/v1722954962561/3a713fce-5b5f-4683-80a1-9b351d901707.png align="left")

### Step 4. Start your App's Dev Server

Ensure your app is running on your preferred port. For example, if your React app is locally available via [`http://localhost:5173`](http://localhost:5173), run the following command in a terminal at the root of your computer:

```bash
ngrok http 5173
```

This command forwards your local server to a hosted URL accessible via any device in any location. The URL should look something like this: [`https://1093-102-89-47-254.ngrok-free.app/`](https://1093-102-89-47-254.ngrok-free.app/)

![ngrok forwarded port running](https://cdn.hashnode.com/res/hashnode/image/upload/v1722955008706/e4775ef5-f27e-4bf6-b4c9-cd0ec809a952.png align="left")

Now you can view your site live on your mobile device and share it with others while receiving real-time updates when you make any changes to your app.

> **Note:** Since ngrok runs over the internet, this forwarded port URL is accessible to anyone until you manually kill your app server or ngrok port.

## Summary

Aside from hosting a local server, ngrok can do much more, including:

* Testing webhooks development
    
* Deploying a static application
    
* Skipping CI/CD checks using Kubernetes
    

I hope you enjoyed reading this article and learned something new. If this was helpful, consider sharing it with friends who want to test their site on their mobile phones without the hassle of hosting it.