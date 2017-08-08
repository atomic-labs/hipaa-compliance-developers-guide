# Developers Guide to HIPAA Compliance

## Notes

This is a fork of a Version 1.0 of a TrueVault repo. I found it to be a very concise introduction to HIPAA compliance.

Resources.md was added as a guide to other HIPAA resources. See section 00 of the TOC.

-- eli@tnlabs.ca July 21, 2017

## About

This guide is designed to provide developers with a solid understanding of HIPAA guidelines and their implications for application development.

HIPAA was originally written in 1996, well in advance of the consumer Internet and a decade ahead of the first iPhone. Therefore, many of the rules and provisions deal with security and privacy issues from a world that didn't have a notion of apps, smartphones, and wearables. And while it's been amended to address privacy and security for the web, the complexity and wide-sweeping nature of the law makes teasing out the exact details to ensure compliance a bit cumbersome.

Further, unlike PCI, there is no certification entity that can provide developers a rubber stamp of compliance approval. It's up to developers and companies alike to ensure compliance requirements are implemented properly.

This guide will give you enough information to give you a strong understanding of HIPAA without getting bogged down in the legalese. We've tried to keep it straight forward, written in plain language.

[Read the Introduction](Introduction.md)

## Table of Contents
00 — [Resources](00-Resources.md)
+ [US gov](00-Resources.md#usgov)
  + [Health and Human Services (hhs.gov)](00-Resources.md#hhs)
  + [National Institute of Standard and Technology (nist.gov)](00-Resources.md#nist)
  + [4 Rules of HIPAA](00-Resources.md#four)
+ [Cloud Providers](00-Resources.md#cloud)
  + [AWS](00-Resources.md#aws)
  + [Heroku](00-Resources.md#heroku)
  + [SumoLogic](00-Resources.md#sumo)
  + [TrueVault](00-Resources.md#tv)
+ [Messaging Providers](00-Resources.md#msg)
+ [Articles & Publications](00-Resources.md#articles)
  + [Enforcement & Resolutions](00-Resources.md#enforcement)
  + [Logging](00-Resources.md#logging)
  + [SMS](00-Resources.md#sms)
  + [Data De-Identification](00-Resources.md#deid)
+ [Videos](00-Resources.md#vids)


01 — [Introduction](01-Introduction.md)
+ [2013 Final Omnibus Rule Update](01-Introduction.md#2013-final-omnibus-rule-update)
+ [Why this guide?](01-Introduction.md#why-this-guide)
+ [Who is this guide for?](01-Introduction.md#who-is-this-guide-for)
+ [Build on our work](01-Introduction.md#build-on-our-work)
+ [Questions/Feedback](01-Introduction.md#questionsfeedback)
+ [Mandatory Disclaimer](01-Introduction.md#mandatory-disclaimer)

02 — [What is HIPAA?](02-WhatIsHIPAA.md)
+ [Background](02-WhatIsHIPAA.mdbackground)
+ [2013 Final Omnibus Rule Update](02-WhatIsHIPAA.md#2013-final-omnibus-rule-update)
+ [The Four Rules of HIPAA](02-WhatIsHIPAA.md#the-four-rules-of-hipaa)
+ [Important Terms to Know](02-WhatIsHIPAA.md#important-terms-to-know)
  + [Protected Health Information](02-WhatIsHIPAA.md#protected-health-information-phi)
  + [The Difference Between PHI and Consumer Health Information](02-WhatIsHIPAA.md#the-difference-between-protected-health-information-and-consumer-health-information)
  + [Covered Entity](02-WhatIsHIPAA.md#covered-entity)
  + [Business Associate](02-WhatIsHIPAA.md#business-associate)
  + [No Safe Harbor Clause](02-WhatIsHIPAA.md#no-safe-harbor-clause)

03 — [Do I Need to Be HIPAA Compliant?](03-DoINeedToBeHIPAACompliant.md)
+ [Who Needs to Be HIPAA Compliant?](03-DoINeedToBeHIPAACompliant.md#who-needs-to-be-hipaa-compliant)

04 — [HIPAA Security Rule](04-HIPAASecurityRule.md)
+ [3 Parts to the HIPAA Security Rule](04-HIPAASecurityRule.md#3-parts-to-the-hipaa-security-rule)
  + [Administrative Safeguards](04-HIPAASecurityRule.md#administrative-safeguards)
  + [Technical Safeguards](04-HIPAASecurityRule.md#technical-safeguards)
    + [Access Control Safeguards](04-HIPAASecurityRule.md#access-control-requirements)
    + [Transmission Security](04-HIPAASecurityRule.md#transmission-security)
    + [Audit and Integrity](04-HIPAASecurityRule.md#audit-and-integrity)
  + [Physical Safeguards](04-HIPAASecurityRule.md#physical-safeguards)
    + [Facility Access Controls](04-HIPAASecurityRule.md#facility-access-controls)
    + [Device and Media Controls](04-HIPAASecurityRule.md#device-and-media-controls)
    + [Workstation Security](04-HIPAASecurityRule.md#workstation-security)
+ [Required vs. Addressable Specifications](04-HIPAASecurityRule.md#required-vs-addressable-specifications)

05 — [Becoming HIPAA Compliant](05-BecomingHIPAACompliant.md)
+ [What Does HIPAA Require](05-BecomingHIPAACompliant.md#what-does-hipaa-require)
+ [What it Means for Developers](05-BecomingHIPAACompliant.md#what-it-means-for-developers)
+ [If We're Being Honest](05-BecomingHIPAACompliant.md#if-were-being-honest)

06 — [Who Certifies HIPAA Compliance](06-WhoCertifiesHIPAACompliance.md)
+ [The Short Answer](06-WhoCertifiesHIPAACompliance.md#the-short-answer-is-no-one)
+ [But Texas](06-WhoCertifiesHIPAACompliance.md#but-texas)

07 — [HIPAA Fines](07-HIPAAFines.md)
+ [Unencrypted Data](07-HIPAAFines.md#unencrypted-data)
+ [Employee Error](07-HIPAAFines.md#employee-error)
+ [Data Stored on Devices](07-HIPAAFines.md#data-stored-on-devices)
+ [Business Associates](07-HIPAAFines.md#business-associates)

08 — [Developer Considerations](08-DeveloperConsiderations.md)
+ [Build vs. Buy](08-DeveloperConsiderations.md#build-vs-buy)
+ [Unintended Use Cases](08-DeveloperConsiderations.md#unintended-use-cases)
+ [HIPAA Hosting and Compliance](08-DeveloperConsiderations.md#hipaa-hosting-and-compliance)
  + [Does Using HIPAA Hosting Make My Application HIPAA Compliant?](08-DeveloperConsiderations.md#does-using-hipaa-hosting-make-my-application-hipaa-compliant)
  + [What Data Should Be Stored in HIPAA Compliant Hosting Environments?](08-DeveloperConsiderations.md#what-data-should-be-stored-in-hipaa-compliant-hosting-environments)
  + [What Makes a Hosting Environment HIPAA Compliant?](08-DeveloperConsiderations.md#what-makes-a-hosting-environment-hipaa-compliant)
  + [Network and Application Security](08-DeveloperConsiderations.md#network-and-application-security)
  + [High-Availability and Redundancy](08-DeveloperConsiderations.md#high-availability-and-redundancy)
  + [Required vs. Addressable HIPAA Implementation Specifications](08-DeveloperConsiderations.md#required-vs-addressable-hipaa-implementation-specifications)

09 — [Mobile Applications](09-MobileApplications.md)
+ [Use Cases](09-MobileApplications.md#use-cases)
+ [PHI in the Application](09-MobileApplications.md#phi-in-the-application)
+ [User Communication](09-MobileApplications.md#user-communication)
  + [Email](09-MobileApplications.md#email)
  + [Database/API Calls](09-MobileApplications.md#databaseapi-calls)
+ [Push Notifications](09-MobileApplications.md#push-notifications)
+ [Physical Phone Security](09-MobileApplications.md#physical-phone-security)
  + [Using the Lock Screen](09-MobileApplications.md#using-the-lock-screen)
  + [Enabling Remote Wiping of Lost Phones](09-MobileApplications.md#enabling-remote-wiping-of-lost-phones)

10 — [Wearable Applications](10-WearableApplications.md)
+ [Considerations for Wearables](10-WearableApplications.md#considerations-for-wearables)
  + [Alerts and Notifications](10-WearableApplications.md#alerts-and-notifications)
  + [Default Displays](10-WearableApplications.md#default-displays)
  + [APIs and Data Sharing](10-WearableApplications.md#apis-and-data-sharing)
  + [Medical Devices](10-WearableApplications.md#medical-devices)
  + [Data Encryption](10-WearableApplications.md#data-encryption)
  + [Data Synching](10-WearableApplications.md#data-synching)

11 — [Apple HealthKit and iOS 8](11-AppleHealthKit_iOS8.md)
+ [TrueVault iOS 8 SDK](11-AppleHealthKit_iOS8.md#truevault-ios-8-sdk)
+ [iOS 8 Health-Related Announcements](11-AppleHealthKit_iOS8.md#ios-8-health-related-announcements)
+ [Apple HealthKit Announcements](11-AppleHealthKit_iOS8.md#apple-healthkit-announcements)

12 — [About TrueVault](12-AboutTrueVault.md)
+ [Built for Developers Like You](12-AboutTrueVault.md#built-for-developers-like-you)
+ [HIPAA Compliant](12-AboutTrueVault.md#hipaa-compliant)
+ [BAA + Insurance](12-AboutTrueVault.md#baa--insurance)
+ [Startups](12-AboutTrueVault.md#startups)
+ [Mobile Apps](12-AboutTrueVault.md#mobile-apps)
+ [Web Apps](12-AboutTrueVault.md#web-apps)
+ [Wearable Health Tech Devices](12-AboutTrueVault.md#wearable-health-tech-devices)
+ [Why People Like TrueVault](12-AboutTrueVault.md#why-people-like-truevault)
+ [Try TrueVault for Free](12-AboutTrueVault.md#try-truevault-for-free)


## Conclusion

HIPAA is much more than just encryption. Access control and logging beyond what a standard development environment provides is essential. Everything must be audit ready on demand. Audit compliance and emergency situations should not consume developer time down the road. Developers can't be expected to forsee every legal threat lurking in regulations. Using compliant providers is an investment that should be made at the start of any project.


---

## About TrueVault

TrueVault is a HIPAA compliant API and secure data store that makes meeting the technical safeguard requirements of HIPAA easy for developers. Think of us like Stripe, but instead of payments, we make sure your app is checking all the boxes for HIPAA security and privacy. [Learn more](https://www.truevault.com/)

### TrueVault (Original Disclaimer)

We're not lawyers. Nothing in this guide constitutes legal advice. Talk to one if you have specific questions regarding your application and HIPAA compliance.
