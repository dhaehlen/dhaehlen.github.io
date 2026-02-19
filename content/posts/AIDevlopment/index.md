+++
date = '2026-02-18T16:05:12Z'
draft = true
title = 'AI Development'
+++

The goal is to run AI in development VMs on my Proxmox homelab. 

This project is inspired by a very informative video from Adreas Spiess: 
[Why AI Agents Replaced the Arduino IDE in My ESP32 Projects (Claude Code, Gemini CLI, Codex)](https://www.youtube.com/watch?v=5DG0-_lseR4&t=1218s)

I like coding, I'm torn by spending time on this or simply to code by hand but this is the way the world is
going. Ultimately, I like to code because I like to build things, at the start of this journey I want to see
if AI can help me build the things I want to build faster.

## Why Run in a VM?

Beyond my dislike of poluting my host computer with installs and packages ( this is also why I want to use my
server and docker to containerize all my development environments) I want to give the AI full control 
including the ability to execute command line commands and modify folder structures. Obviuously, this is not 
something I want to allow on my everyday computer (see moltbot nightmare stories).

## What we need:

- [x] Proxmox or Other hypervisor
- [x] A VM (I've gone with Debian)
- [ ] An AI CLI

## AI Agents

I don't want to spend a lot of time choosing which Agent. I am picking Claude code because Andreas
recommended it and he does a lot of ESP32 work which is what I want to use this for first. I may come
back and try out other ones but for now this about AI development in VMs and not which AI to use.

--dangerously-skip-permissions
install superclaude command
--yolo for gemini

- [ ] install curl if not already installed
- [ ] for claude code: curl -fsSL https://claude.ai/install.sh | bash
 
Different from the development containers we are building. The AI agents will need to have the files
stored within the VM. If the project files are not in the VM then the VM would need access throuhg a 
file share to the host which breaks the encapuslation we want.

## Setup Diagram

Pictures are worth 1000 words

```goat
  .-------------.  .------------. 
  | Hypervisor  |  | PC         |
  | .-------. .-|--+ - Terminal |
  | | VM    |<' |  |            |
  | |  -CLI |   |  |            |
  | '-------'   |  |            |
  '-------------'  '------------'
```

I'm using a Windows Terminal because its easy to get on Windows.

## Questions to Answer

- [ ] Do we want or need a desktop environment?
- [ ] log into Claude CLI through command line?
- [ ] What is the best way to set up a file share?
- [ ] Why do we want a file share?

## Answered Questions

- [x] How to access the AI CLI running in VM?
    - we have a terminal on the computer we want to work from (in my case it is windows terminal on my
	windows machines) and then we use ssh to access the VM which is running the AI CLI. From the terminal
	we can then execute commands through the ssh connection on the VM and controll the AI.

## ToDo

- [ ] intall git on VM
- [ ] set up a file share
- [ ] improve SSH with ssh key
