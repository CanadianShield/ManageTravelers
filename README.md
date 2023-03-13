# Introduction

We often get questions like “How can I give access to travelers without opening access to everybody?”, “Can we stop our travelers from downloading files outside our countries of operation?”, “How can I ensure that my travelers know about our internal travel policies?”, “I don’t want to have a big impact on our helpdesk/identity management team, would there be a solution that reduces that impact?” 

# Conditional Access

Let’s start with the question “How can I give access to travelers without opening access to everybody?” 

An effective way to carry out that goal would be to create a Conditional Access Policy (CAP) that blocks sign-ins from anywhere except your operation countries and then use the exclusions on that CAP to allow people to sign-in from anywhere. 

This approach works quite well, but if we want to reduce the risk, would it not be better to give access to only the countries that they will visit? Yes, but if we want to create one policy per country, we will probably reach the maximum number of policies that a tenant can have (195 policies: [Plan an Azure Active Directory Conditional Access deployment - Microsoft Entra | Microsoft Learn](https://learn.microsoft.com/en-us/azure/active-directory/conditional-access/plan-conditional-access#minimize-the-number-of-conditional-access-policies)). Another limitation that we have is that some users don’t know exactly the list of countries that they will travel to (ex: the user plans to go to Belgium and Germany but have not planned that they will pass through France and that the flights taken will pass by the Netherlands). Instead of going with one CAP for each country we will solve those limitations by creating categories, each one with a different CAP: 
- Continents (Africa, Antarctica, Asia, Europe, North America, Oceania, South America) 
- Anonymous and blocked countries 

The next question that we will solve is “Can we stop our travelers from downloading files outside our countries of operation?” 

We can do it by blocking the possibility to use the Modern and Desktop apps while outside the operation countries but allowing access from browsers in a session that does not have the possibility to download files. We will have one CAP for each of those requirements. 

Note that a file already present on the user’s device will not be protected by this. The use of device encryption (ex: BitLocker) and DLP (ex: Azure Information Protection) is recommended.  

“How do I ensure that my travelers know about our internal travel policies?”, this question can be answered in many ways: 
- a member of the security team could send an email before the travel. 
- it could be part of the onboarding process for new employees. 
- etc. 

We want this step to be as easy as possible for everybody so we will create Terms of use that the user will need to read and accept the first time they sign-in outside the operation countries. 

 
Here's a diagram showing the access for 4 different cases as examples: 
![image](./images/CAP-diagram.png)
















# Identity Governance



# Credit

Mathias Dumont (Microsoft)

Paul Morin (Microsoft)



