# MISP - Malware Information Sharing Platform

MISP is an open-source threat intelligence platform designed to improve the sharing and analysis of cyber threat data. It facilitates collaboration between organizations, CERTs (Computer Emergency Response Teams), ISACs (Information Sharing and Analysis Centers), and other security professionals by providing a centralized hub for storing, sharing, and correlating threat intelligence.

## Features
- **Data Sharing**: Securely share and collaborate on threat intelligence with trusted partners and communities.
- **Threat Intelligence Storage**: Centralized repository for storing indicators of compromise (IoCs), malware samples, attack patterns, and more.
- **Correlation and Enrichment**: Automatically correlates data to identify relationships between different threats, actors, and campaigns.
- **Standards Compliant**: Fully supports open standards like **STIX** (Structured Threat Information Expression) and **TAXII** (Trusted Automated Exchange of Indicator Information) for seamless data exchange.
- **API Integration**: RESTful API for easy integration with SIEMs, firewalls, endpoint protection, and other cybersecurity tools.
- **Community Driven**: Open-source and community-oriented, with active contributions from a wide range of organizations.

## Use Cases
- **Incident Response**: Use MISP to enhance the response to ongoing incidents by leveraging shared threat data.
- **Threat Hunting**: Empower threat hunters with enriched IoC data to proactively search for potential attacks in your network.
- **Malware Analysis**: Share and retrieve detailed information about malware families, behaviors, and mitigation strategies.
- **Collaboration**: Enable collaboration between different organizations, enhancing the collective defense against emerging threats.

![image](https://github.com/user-attachments/assets/442e951b-faba-40e7-8262-4990a88a9abc)

## MISP Core Functionalities

MISP provides several core functionalities that are key to its operation:

1. **IOC Database**: Stores both technical and non-technical information related to malware samples, incidents, attackers, and intelligence.
2. **Automatic Correlation**: Identifies relationships between attributes and indicators from malware, attack campaigns, or analysis.
3. **Data Sharing**: Facilitates sharing information using different distribution models across multiple MISP instances.
4. **Import & Export Features**: Supports importing and exporting events in various formats for integration with other systems, such as NIDS, HIDS, and OpenIOC.
5. **Event Graph**: Displays the relationships between objects and attributes identified in events.
6. **API Support**: Allows integration with custom systems for fetching and exporting events and intelligence.

## Common Terms in MISP

The following terms are frequently used within MISP and are essential to understanding its functionalities:

- **Events**: A collection of contextually linked information.
- **Attributes**: Individual data points associated with an event, such as network or system indicators.
- **Objects**: Custom compositions of attributes.
- **Object References**: Relationships between different objects.
- **Sightings**: Time-specific occurrences of a data point or attribute detected to enhance credibility.
- **Tags**: Labels attached to events or attributes.
- **Taxonomies**: Classification libraries used to tag, classify, and organize information.
- **Galaxies**: Knowledge base items used for labeling events or attributes.
- **Indicators**: Information pieces that detect suspicious or malicious cyber activity.


## Example Workflow
1. **Data Ingestion**: Threat data (hashes, domains, IPs, TTPs, etc.) is ingested into the platform.
2. **Data Correlation**: MISP automatically correlates and enriches the data with context, such as attack patterns or related threat actors.
3. **Sharing**: The enriched threat intelligence is shared securely with trusted partners or communities.
4. **Action**: Organizations take action by updating security measures, creating detection rules, or investigating ongoing attacks.

## TASK 3 Using The System

## MISP Dashboard Overview

The analyst’s view of MISP provides essential functionalities to track, share, and correlate events and IOCs identified during investigations. The dashboard’s menu offers several options, which we will explore in detail:

1. **Home Button**: Takes you back to the application’s start screen, the event index page, or a custom home page set via the star icon in the top bar.
   
2. **Event Actions**: MISP organizes all malware data as an event object, which is described by its associated attributes. The Event Actions menu provides access to functionality related to:
   - Creation, modification, and deletion of events
   - Publishing, searching, and listing events and attributes.

3. **Dashboard**: Allows you to create a custom dashboard using widgets, tailored to your needs.

4. **Galaxies**: A shortcut to the list of MISP Galaxies available on the MISP instance. More information on this is available in the Feeds & Taxonomies Task.

5. **Input Filters**: Input filters control how data is entered into MISP. Administrators can define rules for:
   - Attribute entry validation by type
   - Regular expression replacements and blocklists for specific values
   - Blocking certain values from being exported.
   
   Users can view these rules, while administrators can modify them.

6. **Global Actions**: Provides access to general information about MISP and your current instance, including:
   - Profile management
   - Access to the manual, news, and terms of use
   - A list of active organizations on the instance with a histogram of their contributions by attribute type.

7. **MISP**: A simple link to your base URL for easy navigation.

8. **Name**: The auto-generated name (from your email address) of the currently logged-in user.

9. **Envelope**: A link to your User Dashboard, where you can check notifications and recent changes, including proposals received for your organization.

10. **Log Out**: The button to log out and end your session immediately.

![image](https://github.com/user-attachments/assets/2608ebe8-9c78-4c65-a5bf-232974504c2d)

## Event Management in MISP

The **Event Actions** tab is where analysts create malware investigation correlations by adding descriptions and attributes related to the investigation. The process can be broken down into three major phases:

1. **Event Creation**
2. **Populating Events with Attributes and Attachments**
3. **Publishing**

In this section, we’ll follow the process to create an event based on an investigation of **Emotet Epoch 4 infection** with **Cobalt Strike** and **Spambot**, sourced from **malware-traffic-analysis.net**. The following steps outline the process.

### 1. Event Creation

Initially, events serve as a storage for general information about an incident or investigation. To create an event:

- Click the **Add Event** button.
- Provide a description of the event.
- Set the appropriate **time** and **risk level** for the incident.

Next, specify the **distribution level** for the event on the MISP network and community. MISP offers the following distribution options:

- **Your Organisation Only**: This restricts visibility to members of your organisation.
- **Community-Only**: Visible to users in your MISP community, including your organisation, organisations on this MISP server, and other organisations running MISP servers that synchronise with this server.
- **Connected Communities**: Visible to users in your MISP community, including organisations on this MISP server, organisations on MISP servers synchronising with this server, and hosting organisations of servers two hops away.
- **All Communities**: This shares the event with all MISP communities, allowing it to propagate freely between servers.

Additionally, MISP allows you to add a **sharing group**, where you can define a predefined list of organisations with which to share the event.

![image](https://github.com/user-attachments/assets/9dad66a7-d970-4732-847c-5e1813a4e8f5)

Event details can also be populated by filling out predefined fields on a defined template, including adding attributes to the event. We can use the email details of the CobaltStrike investigation to populate details of our event. We will be using the Phishing E-mail category from the templates.

![image](https://github.com/user-attachments/assets/e3df158e-9d6a-4361-b073-8cd58c170205)

## Attributes & Attachments in MISP

Attributes can be added manually or imported from other formats, such as **OpenIOC** and **ThreatConnect**. To add them manually, click the **Add Attribute** button and populate the form fields.

### Key Options to Note:

1. **For Intrusion Detection System (IDS)**: 
   - This option allows the attribute to be used as an IDS signature when exporting **NIDS** data, unless it overrides the permitted list.
   - If not set, the attribute is considered as **contextual information** and will not be used for automatic detection.

2. **Batch Import**: 
   - If multiple attributes of the same type need to be entered (e.g., a list of IP addresses), you can add them all in the same value field, separated by line breaks.
   - This enables the system to create separate lines for each attribute.

### Example:

In our example, we add an **Emotet Epoch 4 C2 IP address** associated with the infection as our attribute, which was obtained from the **IOC text file**.


![image](https://github.com/user-attachments/assets/09e38f53-dcc7-40d6-8610-973e8e10f9a6)

The analyst can also add file attachments to the event. These may include malware, report files from external analysis or simply artefacts dropped by the malware. We have added the Cobalt Strike EXE binary file to our event in our example. You also have to check the Malware checkbox to mark the file as malware. This will ensure that it is zipped and passworded to protect users from accidentally downloading and executing the file.


![image](https://github.com/KAmii-cxo/MISP/blob/main/gifs/0_0CLOTPuuEJmkg3Uo.gif)

## Publish Event

Once the analysts have created events, the organisation admin will review and publish those events to add them to the pool of events. This will also share the events to the distribution channels set during the creation of the events.


![image](https://github.com/KAmii-cxo/MISP/blob/main/gifs/publishevent.gif)

## Task 4: Feeds & Taxonomies

### Feeds

Feeds are resources that contain indicators, which can be imported into MISP to provide attributed information about security events. These feeds help analysts and organisations stay updated with continuously evolving threats and adversaries, supporting proactive defense against attacks.

MISP Feeds allow you to:

- **Exchange Threat Information**: Share and receive valuable threat data across different platforms.
- **Preview Events**: View events along with their associated attributes and objects.
- **Select and Import Events**: Choose specific events to import into your instance for further analysis.
- **Correlate Attributes**: Identify and correlate attributes between events and feeds to uncover patterns and relationships.

Feeds are enabled and managed by the **Site Admin**, allowing analysts to access event and indicator data efficiently.


![image](https://github.com/KAmii-cxo/MISP/blob/main/gifs/feed%20n%20taxonomies.gif)

## Taxonomies

A taxonomy is a means of classifying information based on standard features or attributes. On MISP, taxonomies are used to categorise events, indicators and threat actors based on tags that identify them.

![image](https://github.com/user-attachments/assets/21929726-177b-443c-9cb0-8eb0c74630f5)

Taxonomies play a crucial role in MISP by helping analysts classify and process events effectively. Analysts can use taxonomies to:

1. **Set events for further processing** by external tools such as VirusTotal.  
2. **Ensure events are classified appropriately** before the Organisation Admin publishes them.  
3. **Enrich intrusion detection systems (IDS)** export values with tags that fit specific deployments.  

#### **Taxonomy Structure**
Taxonomies in MISP are expressed using machine tags, which consist of three key components:

- **Namespace**: Defines the tag's property to be used.  
- **Predicate**: Specifies the property attached to the data.  
- **Value**: Provides numerical or textual details that map to the property.  

**Example (Source: MISP):**
```
Namespace:  threat 
Predicate:  level 
Value:      high
```
Taxonomies are listed under the Event Actions tab. The site admin can enable relevant taxonomies.

![image](https://github.com/KAmii-cxo/MISP/blob/main/gifs/taxonomies.gif)

## Tagging

Information from feeds and taxonomies, tags can be placed on events and attributes to identify them based on the indicators or threats identified correctly. Tagging allows for effective sharing of threat information between users, communities and other organisations using MISP to identify various threats.

In our CobaltStrike event example, we can add tags by clicking on the buttons in the Tags section and searching from the available options appropriate to the case. The buttons represent global tags and local tags, respectively. It is also important to note that you can add your unique tags to your MISP instance as an analyst or organisation that would allow you to ingest, navigate through and share information quickly within the organisation.

![image](https://github.com/KAmii-cxo/MISP/blob/main/gifs/Tagging.gif)

## Tagging Best Practices

## Tagging at Event Level vs Attribute Level
Tags can be added to an event and attributes. Tags are also inheritable when set. It is recommended to set tags on the entire event and only include tags on attributes when they are an exception from what the event indicates. This will provide a more fine-grained analysis.

## The Minimal Subset of Tags
The following tags can be considered a must-have to provide a well-defined event for distribution:

- **Traffic Light Protocol**: Provides a colour schema to guide how intelligence can be shared.
- **Confidence**: Provides an indication as to whether or not the data being shared is of high quality and has been vetted so that it can be trusted to be good for immediate usage.
- **Origin**: Describes the source of information and whether it was from automation or manual investigation.
- **Permissible Actions Protocol**: An advanced classification that indicates how the data can be used to search for compromises within the organisation.

TASK 5
   1. First, set PupyRAT at Filter . The event ID is 1146
      ![image](https://github.com/user-attachments/assets/f4d5499c-e2c0-4a10-9737-9ceffb55bebe)
      ![image](https://github.com/user-attachments/assets/9dfa6fa6-15c5-4e56-b583-a2f7d0c93356)

   2. Remote Access 
   3. The IP address is 89.107.62.39

      ![image](https://github.com/user-attachments/assets/ecd25faf-6e3d-4aab-996b-106ad530c733)

   4. Magic Hound is known to use this form of attack. 

      ![image](https://github.com/user-attachments/assets/95f301b2-ae22-460f-b85b-7ae61045281e)

   5. OSINT is the answer

      ![image](https://github.com/user-attachments/assets/52c10598-aefd-488e-8b7a-93b30bd27d1a)

   And that's all about MISP that we learn just now. It's time to practise in the real-world, detecting threats and protecting digital enviroment. For some additional infos, you can check below and dig up more. 
         
## Additional Resources

   1. [MISP Book](https://www.circl.lu/doc/misp/)
   2. [MISP GitHub](https://github.com/MISP/)
   3. [MISP Training module 1](https://www.youtube.com/watch?v=aM7czPsQyaI)
   4. [MISP Training module 2](https://www.youtube.com/watch?v=Jqp8CVHtNVk)

