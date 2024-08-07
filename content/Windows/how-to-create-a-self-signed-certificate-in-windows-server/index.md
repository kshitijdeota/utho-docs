---
title: "How to Create a Self-Signed Certificate in Windows Server"
date: "2023-06-13"
Title_meta: GUIDE TO Create a Self-Signed Certificate in Windows Server
Description: Learn how to create a self-signed certificate in Windows Server with this step-by-step guide. Follow instructions to generate a self-signed SSL/TLS certificate using PowerShell or the Microsoft Management Console (MMC), enabling secure communication and testing within your server environment.
Keywords: ['Windows Server', 'self-signed certificate', 'SSL certificate', 'TLS certificate', 'certificate creation', 'server security']
Tags: ["Windows Server", "Self-Signed Certificate", "SSL Certificate", "TLS Certificate", "Certificate Creation", "Server Security"]
icon: "windows"
date: "2024-03-07T17:25:05+01:00"
lastmod: "2024-03-07T17:25:05+01:00" 
draft: false
toc: true
aliases: ['/Windows/how-to-create-a-self-signed-certificate-in-windows-server/']
---

![](images/How-to-Create-a-Self-Signed-Certificate-in-Windows-Server-1024x576.jpg)

### INTRODUCTION

In cryptography and computer security, self-signed certificates are public key certificates that are not issued by a certificate authority. These self-signed certificates are easy to make and do not cost money. However, they do not provide any trust value. On modern Windows versions ([Windows Server](https://utho.com/docs/tutorial/how-to-install-ssl-on-windows-server/) 2022/2019/2016/2012R2) you can create a self-signed certificate using the built-in PowerShell cmdlet `[New-SelfSignedCertificate](https://learn.microsoft.com/en-us/powershell/module/pki/new-selfsignedcertificate?view=windowsserver2022-ps)` without using additional tools. In this tutorial, we will learn how to Create a Self-Signed Certificate in Windows Server.

#### Prerequisites

- Windows Server

- [PowerShell](https://en.wikipedia.org/wiki/PowerShell) with Administrator

- Internet connectivity

Step 1. Login to your Windows Server

Step 2. Open PowerShell with Administrator

![Create a Self-Signed Certificate](images/Screenshot_11-14.png)

Step 3. Run the following command to generate a self-signed certificate

![](images/Screenshot_1-38-1024x527.png)

Step 4. We will edit the domain name and certificate location according to our preference.

![Create a Self-Signed Certificate](images/Screenshot_2-48-1024x527.png)

Step 5. Self-signed certificate generated.

![](images/Screenshot_3-36-1024x527.png)

Step 6. Check our recently generated self-signed certificate by running **certlm.msc** in run.

![Create a Self-Signed Certificate](images/Screenshot_4-38-1024x477.png)

Thank You!
