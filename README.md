# OWASP Juice Shop Challenges

## Description
A repository with a series of selected OWASP Juice Shop challenge solutions and write-up documentation.

> [!WARNING]
>
> This is only for learning purposes.
>
> Only do this in a safe, isolated environment (like a VM).

## Table of Contents

1. [Introduction](#introduction)
2. [Challenges](#challenges)
    - [GDPR Data Theft](#gdpr-data-theft)
    - [Product Tampering](#product-tampering)
    - [Reset Bender's Password](#reset-benders-password)
3. [Project Checklist](#project-checklist)

## Introduction
OWASP Juice Shop is a deliberately insecure web application designed for security training, CTFs, and tool testing. It is a learning platform that helps developers, security professionals, and enthusiasts understand common web application security issues.

More information: [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)

## Challenges

### GDPR Data Theft

__Category__: Sensitive Data Exposure

__Difficulty__: :star: :star: :star: :star:

__Loom Video__: https://www.loom.com/share/761f5fa5df574ca396f5dd5613e8966a?sid=fd0c6da3-8d4b-4bad-9e67-f27e2dc70e2a

Steal someone else's personal data without using Injection. The OWASP Juice Shop is compliant with General Data Protection Regulation (GDPR) and has a `data request export function` that can be exploited to find a flaw and retrieve personal data.

Write-up document: [gdpr_data_theft](challenges/gdpr_data_theft/gdpr_data_theft.md)

### Product Tampering

__Category__: Broken Access Control

__Difficulty__: :star: :star: :star:

__Loom Video__:

Change the href of the link within the OWASP SSL Advanced Forensic Tool (O-Saft) product description to https://owasp.slack.com.

Write-up document: [product_tampering](challenges/product_tampering/product_tampering.md)

### Reset Bender's Password

__Category__: Broken Authentication

__Difficulty__: :star: :star: :star: :star:

__Loom Video__: https://www.loom.com/share/140a7ed8cc7d4075b19d8f3b117d0b88?sid=bdf66aef-a838-44dc-8aec-e44afad1f3ea

Reset Bender's password via the Forgot Password mechanism with the truthful answer to his security question.

Write-up document: [reset_benders_pass](challenges/reset_benders_pass/)

## Project Checklist

- 📄 [Checklist (PDF)](docs/checklist.pdf)
