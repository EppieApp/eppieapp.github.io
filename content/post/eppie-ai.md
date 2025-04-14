+++
title = 'Local AI Assistant in Email: How to Use'
date = 2025-04-09T13:07:31+04:00
draft = false
summary = "We have added AI to Eppie. Let's talk about why and how to try it in the latest build."
+++

Great news! We’ve added AI to Eppie. Let's talk about why and how to try it in the latest build.

## Local AI = Private AI

Until recently, we didn’t understand how to deal with convenient and common features that modern email services offer nowadays: semantic search, smart sorting, reliable spam filtering, etc. These are all great inventions - it’s hard to imagine a competitive email service without them. The problem is that this functionality relies on client-server architecture – which, in our opinion, is the root of the evil that Eppie is striving to escape from. A server must peek into the content of your email to tag it, send it to spam, or find something in it. In Eppie, there’s no server; emails are encrypted – and there’s no element in the entire system that could perform this work. This results in very private mail – with quite limited capabilities. A solution suddenly came from AI. But without a server.

In a recent update, we built the ability into Eppie to connect local AI models. Filtering spam, warning about phishing attempts, separating technical notifications from messages from real users, translating, and assisting in writing emails in Eppie will be handled by AI. However, you don’t show emails to anyone; everything works locally, on your computer. This will only make Eppie safer, and there’s no need to sacrifice anything in terms of user experience.

We are currently in the proof of concept stage. The functionality is still very basic: you download a pre-trained language model, give it a task, such as “translate all emails from English to Spanish” – resulting in a simple AI agent that processes incoming messages and generates responses if needed. The most interesting part is the prompt that you create.

The main news is that you can already try it in the latest build. Now we’ll explain how.

## How to Set Up the AI Agent

1. Install the [AI Dev Gallery Preview](https://apps.microsoft.com/detail/9n9pn1mm3bd5?hl=en-GB&gl=GE). This is a Microsoft application for AI developers. It allows downloading language models from [Hugging Face](https://huggingface.co/) - an Open Source AI community repository.

{{< figure src="/ai_tut/AIDevGal.png" >}}

2. In the AI Dev Gallery under the *Models* tab, select a model. Right now just pick *Phi 4 mini*, the first in the list. Later on, you can try others – Eppie currently supports: *gemma*, *deepseek*, *llama*, *mistral*, *phi*, and *qwen*. If you’re already familiar with the topic and want to try a specific model, search for it in the search bar.

{{< figure src="/ai_tut/AIDevGalModels.png" >}}

Pay attention to what processor the model runs on. If you have a powerful graphics card, choose larger models that run on GPU. Otherwise, look for smaller ones for CPU.

You can also skip installing the AI Dev Gallery and download models manually from the [site](https://huggingface.co/models?library=onnx&search=gemma) (in this case, be sure to specify ONNX library in the search).

{{< figure src="/ai_tut/HuggingFace.jpg" >}}

3. Go to settings and check the path in the *Model Cache* section where models are downloaded. You can also delete unnecessary models there.

​	If you download a model from the website, it needs to be unpacked into a folder named after the 	model – Eppie is currently trying to understand what model is loaded by the folder name.

4. Open Eppie. AI is supported in version 1.0.150.0 and above. You can download the fresh release from [Microsoft Store](https://apps.microsoft.com/detail/Eppie%20Mail%20Preview/9n3r8xkz16c5?mode=direct&cid=github) or [GitHub](https://github.com/Eppie-io/Eppie-App/releases/latest/download/Eppie.App-x86-x64-ARM64.msixbundle). Go to Identity Manager. Select *Connect Service* / *Local AI Agent (Beta)*.

{{< figure src="/ai_tut/IdManager.png" >}}

5. Select *Import local AI model* and specify the path where you downloaded the model (navigate to the deepest nested folder). Choose an agent template – let's start with *Sentiment Analyzer*. If you want, you can change or add to the prompt. The other settings can be left as is for now.

{{< figure src="/ai_tut/AgentSetup.png" >}}

By the way, you can add multiple agents with different tasks.

6. In the mailbox, select an incoming email. In the top right corner, a button named *AI agent* will appear. Click it, select an agent from the list, and watch it complete the task. Now you have an AI agent set up that will work locally on your device.

{{< figure src="/ai_tut/SentimentEng.png" >}}

Go ahead and experiment with the settings.

Connect more agents. It doesn’t really matter what you choose in the template menu – what matters is what you write in the prompt. 

Try to chain them using the *Pre-processing* and *Post-processing* menus. You can, for example, use a translator agent as a post-processor, so whatever the main agent outputs is then translated to your native language.
Try adjusting the parameters *Top P*, *Top K*, *Temp*. In short, they determine the creativity of the model. If you set them too high, AI produces unreadable garbage; if too low – predictable responses. Somewhere in between, you can achieve something interesting.

If you bind the agent to a specific mailbox, it will automatically perform its work with each incoming email.

Do not enable *Allow sending emails* yet, otherwise the agent might start conversing with itself. Or use a test mailbox that you don’t mind experimenting with.

------

Well, that's basically it. Visit our [GitHub](https://github.com/Eppie-io/Eppie-App), download Eppie (agents currently only work in the UWP build for Windows, but we will soon release new builds for Linux and MacOS). Create issues and [subscribe](https://eppie.io/). Thank you!
