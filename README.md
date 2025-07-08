# OWASP Juice shop challenges.

## Description
A repository with a series of selected OWASP juice shop challenges solutions and write-up documentation.

> [!WARNING]
>
> This is only for learning purpuses.
>
>Only do this in a safe, isolated environment (like a VM).

## Table of Contents

1. [Introduction](#introduction)
2. [Challenges](#challenges)
    - [GDPF Data Theft](#gdpf-data-theft)
    - [Product Tampering](#product-tampering)
    - [Reset Bender’s Password](#reset-benders-password)

4. [Project Checklist](#project-checklist)

## Introduction.
OWASP Juice Shop is a deliberately insecure web application designed for security training, CTFs, and tool testing. It is a learning platform that helps developers, security professionals, and enthusiasts understand common web application security issues.

More information [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/).


## Challenges.

### GDPR Data Theft.

__Category__: Sensitive Data Exposure

__Difficulty__: :star: :star: :star: :star:
	
Steal someone else’s personal data without using Injection. The OWASP juice shop is complient with general data protection regulation (GDPR) and has a `data request export function` that explioted to find a flaw and retrieve personal data.

Write-up document: [gdpr_data_theft](challenges/gdpr_data_theft/gdpr_data_theft.md).

### Product Tampering.

__Category__: Broken Access Control

__Difficulty__: :star: :star: :star:

Change the href of the link within the OWASP SSL Advanced Forensic Tool (O-Saft) product description into https://owasp.slack.com. 

Write-up document: [product_tampering](challenges/product_tampering/product_tampering.md).

### Reset Bender’s Password.

__Category__: Broken Authentication

__Difficulty__: :star: :star: :star: :star:

Reset Bender’s password via the Forgot Password mechanism with the truthful answer to his security question.

Write-up document: [](challenges/reset_benders_pass/).

## Project Checklist

- 📄 [Checklist (PDF)](docs/checklist.pdf)
