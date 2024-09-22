In this blog post, we will go through a formal STRIDE threat modeling session. There are multiple different approaches to threat modeling: threat modeling as code, software diagramming tools, threat modeling tools, ad-hoc unstructured threat modeling, and formal threat modeling using AWS Threat Grammar and STRIDE. The point is, there is no one-size-fits-all solution.

In this blog post, I will be utilizing AWS Threat Grammar and STRIDE because I believe they are a good fit for threat modeling workflows. However, it's important to understand that the choice of approach should be based on the specific requirements and context of your project.

## Overview
- Different kinds of threat models
- What to include in our threat model?
- Understanding the workflow
- How to build comprhensive threat models?
- Threat Actors
- Threats
- Mitigations
- Compliance
- Scaling our threat models
- The Application of AI in threat modelling
- Reusable Markdown version

## Different kinds of threat models

Security engineers perform threat modeling on various scopes, such as systems of systems, infrastructure, cloud environments, applications, and microservices. The scope can range from extensive and high-level to specific functions. However, it's always worth conducting threat modeling for sensitive and critical functionalities, with checkout and payment functionalities being a prime target for threat modelling activities.

In our case, we've decomposed our threat model to focus on the smallest possible workflow. This makes it more reusable and accessible for as many developers as possible. Specifically, **we'll be conducting threat modeling on one specific workflow: the cart checkout functionality using Stripe.**

## What to include in our threat model?
Our Checkout workflow does not exist in isolation. It is part of a larger application or group of microservices that customers interact with before they reach the checkout workflow. There is a shop functionality, an authentication/authorization system, a system used by support employees internally to resolve customer issues, a monitoring solution, and so on. All these functionalities and systems are directly or indirectly connected to our checkout functionality.

For the sake of reusability, we're focusing our threat modeling efforts on a specific workflow. Consequently, certain attacks from adjacent systems, applications, and microservices connected to our checkout feature are considered out-of-scope for this threat model.

For instance, let's consider a support system utilized by internal employees to assist customers with purchase inquiries, which might be directly linked to our checkout system. In such a scenario, if a support employee downloads cracked software onto their device, it could become infected. Subsequently, an adversary could exploit the infected support device to gain access to our cart logs and other sensitive data

## Understanding the workflow
You cannot threat model what you don't understand. Before my threat modeling session with the developers, I reviewed the official Stripe Checkout Documentation and explored the code snippets. Armed with a basic understanding of the workflow, I set myself up for success. This preparation allowed me to follow up during the meeting, ask informed questions, and engage in meaningful discussions with the team.

Here is an image from the official stripe documentation.
[]

## How to build comprhensive threat models?
Defenders need to think about everything, while an attacker only needs to find one security issue to exploit our systems. So, how do you defend effectively?

For starters:

- **Read the documentation**: If possible, implement the workflow yourself to gain hands-on experience.
- Follow security best practices published by Stripe. Don’t reinvent the wheel—many smart people have contributed to these guidelines, so make good use of them.
- Communicate with your developers about the flow, risks, and mitigations. You'll be surprised by how their insights can help defend against threats or inspire you to identify additional vulnerabilities.

## Threat Actors
Those are the different threat actors targeting our system:

- External user
- Internal employee
- Malicious process running on the same host node
- Malicious NPM package contributor
- Malicious JavaScript library contributor

## Threats

## Mitigations


## Compliance
Every organization has its own compliance needs, contractual obligations, third-party requirements, and more. The list is endless. As a security engineer, you must ensure your threat models address these needs. They are a crucial factor in your security features.

[]

> **DISCLAIMER**: This is not legal advice. The following information is for educational purposes only and should not be relied upon as legal or compliance advice. Please conduct your own due diligence.

In my case, the company was very small and did not have PCI requirements. However, I did some due diligence and discovered that Stripe requires customers using Stripe Checkout to complete the PCI SAQ A survey and submit it annually. After some back and forth with the Stripe team, I learned that Stripe Checkout customers might be eligible for an auto-generated survey provided by Stripe, which they can upload. So, for now, there are no compliance requirements for me. For now!! Always stay vigilant for changes in requirements and scope.

[]

[]

## Scaling our threat models
Given our threat model, I recommend documenting this in Confluence or your preferred internal documentation tool. If your organization is large enough, consider hosting AWS Threat Composer and importing these models into it. The whole point of decomposing threat models is reusability, so let's ensure these threat models can be utilized by other teams as well!

## The Application of AI in threat modelling
While GPT-4 could not generate a useful threat model, it often explained STRIDE or provided generic information about threat modeling.

That being said, it was very useful in ensuring the semantic and grammatical correctness of the threat model. Additionally, it rephrased the threats to comply with AWS threat grammar consistently. With a little bit of guidance, it was quite capable of identifying which mitigations blocked which threats.

## Reusable Markdown version
If you are looking for a ready-to-use Markdown version, please check out the GitHub repository for this threat model at: https://github.com/akenofu/Threat-Modeling-Stripe-checkout/
ح[]
جد
جد
