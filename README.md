# TeamAI2


 
Table of Contents
1.    About Us:	3
2.    Thanks	3
3.     The Problem Statement/Opportunity—Road Warrior	3
4.    Our Vision for Road Warrior	3
5.    Our Approach/Process to the Solution	3
6.    Our Proposed Solution—Initial Draft	4
a)      Architecture Characteristics of the Road Warrior Application:	4
b)     Architecture Style of the Road Warrior Application:	5
c)      Logical Components of the Road Warrior Application:	6
d)     Architecture Decisions Set for the Road Warrior Application:	7
7.    References	8

 
1.    About Us:
We are a team of Consulting Partner, Sr. Architects and Lead Developers from Wipro. We go by the name AI2 representative of the practice that we lead at Wipro—AI, Automation & Integration. AI2 is “Architecture Insights too.”
2.    Thanks
We wanted to express our sincerest pleasure and thanks for this Architecture Kata Event. We have grown up in India and in the industry referring to O’Reilly books. There have been multiple pleasant memories. We have been following the rich set of ideas (earlier books then blogs, videos etc) that have been brought in by industry luminaries such as Martin Fowler, Mark Richards, Neal Ford, Sam Newman, Rebecca Parsons, and the list goes on. O’Reilly is a great learning platform, always.
In the context of this Architecture Kata 2023, we are excited to be part of. We are looking forward to a lot of learning along with other software architecture practitioners form the industry, being able to exercise a lot of architecture thinking and hands on architecture while also refreshing some of the great ideas and advice from our favorites Neal & Mark & the recommended playlists. Communication is a necessary skill and there was a great set of advice/tips in the book Communication Patterns by Jacqui Read. It was also a pleasure to meet Jacqui Read, Clare Sudbery & Robin Losey briefly in the Kata Kick off meet. We are sure to learn a lot from their real-life experiences and lookouts.
Presenter/Co-ordinator?
In here, we would also like to mention Kunal Bharadwaj from O’Reilly for being our mentor and guiding us/supporting us.
3.     The Problem Statement/Opportunity—Road Warrior
 
4.    Our Vision for Road Warrior
We have a vision for the Road Warrior App. It is to “Make Life’s Journey better one trip at a time.”
5.    Our Approach/Process to the Solution
Since the time was limited— (<5 calendar days) and our team was distributed and remote, we needed a well-defined process to do the Kata as well as work/iterate on the solution.
Keeping the end in mind and the end date, we organized our schedules for individual thought and arranged/participated in multiple Kata Sessions to deliberate on the solution collectively.
We made constant references to the notes from the Kick Off Event as well as the various chapters/books/videos included in the playlist. It helped us refresh some of the architectural thinking and concepts.
Amongst others, it included the
1.       Architecture Dimensions
2.       Architecture Characteristics Worksheet
3.       Logical Component Identification Process
4.       Architecture Decision Records Template
5.       Architecture Styles & Capabilities Comparison
We have made liberal use of paper & pencil/erasure offline following the analog before digital paradigm. We used our Wipro Microsoft Teams for collaboration/calls and draw.io for all the finalized diagrams.
We sincerely believe that software architecture is an iterative model. There should be continuous architecture review and governance. In that spirit, we understand that our solution may have missed certain critical aspects—we call them blind spots. And we are hopeful that by continuing to follow this architecture kata along with others from the industry and the august team, we will be able to create a better point of view/thinking.
We therefore call our proposed solution as our initial draft/first iteration outcome.
6.    Our Proposed Solution—Initial Draft
A software architecture is best described by its 4 dimensions, namely the architecture characteristics, the architecture structure and style, the logical components & the set of architecture. So, in our proposed architecture for the Road Warrior application, we cover these dimensions one after the other.
a)      Architecture Characteristics of the Road Warrior Application:
 
Architecture characteristics form the foundation of a software architecture as they help determine the architectural decisions and trade-offs and thereby also influence the architecture style chosen. Based on the requirements and the additional context provided about the Road Warrior Application, we arrived at the following list of architecture characteristics.
The Road Warrior application is expected to have an user base of 15 Million and atleast 2 Million active users every week. This requires scalability as an important architecture characteristic. Since the target users are travelers, there would be seasonal demands leading to elasticity as another important characteristic.
Users must be able to access the Road Warrior application at all times. There is an explicit allowance of max 5 min only of unplanned downtime per month. Going by the 5 9s calculation, high availability or availability thus becomes another architecture characteristic.
Users access the Road Warrior Application via web as well as mobile. There is an expected response time of 800 ms for the web and the first contentful paint for mobile is under 1.4 sec. (*First contentful paint measures the time it takes for a webpage to load on the mobile device.) Clearly, performance (responsiveness) is sought as an architectural characteristic/capability.
Other than this, we find that the Road Warrior application must interface with multiple systems—travel agencies, travel systems such as SABRE and APOLLO for real time updates and special use cases such as Social Mediums for Trip Share. Similarly, all updates into the Road Warrior system via external interfaces should be within 5 min. This makes integration as an additional architecture characteristic.
We also observe that there are a lot of views, dashboards, end of year summary reports etc. There is also a mention of Road Warrior application gathering analytical data from user trips. This makes data also a first class citizen in the set of architecture characteristics. We also want to add auditability to the mix.
Road Warrior must work internationally. Road Warrior must have the richest user interfaces possible across all deployment platforms. Based on these stated requirements, our architecture solution needs to have portability/deployability.
In addition to these, of course, we have the implicit and default security architecture characteristic and the unstated business requirement of agility and reliability. Agility and Reliability are composite architecture characteristics.
Based on the above initial assessment, we filled the architecture characteristic worksheet template for the Road Warrior Application.
//Include Architecture Characteristic Worksheet
 
 
 
 
 
 
 
 
 
 
b)     Architecture Style of the Road Warrior Application:
Road Warrior is a new startup company. This means it is a greenfield implementation and that is an opportunity to choose the more appropriate architecture structure and style for the Road Warrior Application.
Architecture styles are classified as belonging to 1 of 2 main architectural structures—monolithic and distributed. Monolithic is typically a single deployment unit while a distributed architecture consists of multiple deployment units(usually services). A monolithic architecture suffers from weak operational characteristics such as scalability, fault tolerance and elasticity. So, it would not fit the Road Warrior with reference to the architecture characteristics identified earlier. Thus, monolithic architecture styles such as layered architecture, modular monolith, pipeline architecture and microkernel architecture will not be relevant/appropriate to the Road Warrior.
Having decided the road not to be taken (First ADR), the Road Warrior Architecture Structure to be is Distributed.
(1 ) Distributed Architectures have the following architecture styles—service based architecture, service oriented architecture, space based architecture, microservices architecture, event driven architecture.
Also, whether monolithic or distributed, architectures can also be classified based on partitioning—technical or domain. Microkernel Architecture can fit both. Based on where the changes happen—technical or domain, suitable architecture style can be chosen.
Technical Partitioned Architecture Styles include Layered, Microkernel, Pipeline, Event Driven & Space Based. Similarly, ( 2 )Domain Partitioned Architecture Styles include Microkernel, Microservices, Modular Monolith and Service Based.
Since Road Warrior is a new startup and to focus on travel domain, we see a domain partitioned architecture to be more relevant.
Based on this (1 & 2), the initial list of more appropriate architecture styles include service based and microservices.
Also, microservices because of multiple architecture quanta and relatively low coupling (need to design) can be more agile, scalable and fault tolerant that the Road Warrior App requires. Event Driven Architecture Style (Technical Partitioned) in addition to being scalable and fault tolerant is also very fast and responsive. Therefore, we propose the event driven microservices architecture style which supports both events and request-response interactions for our Road Warrior Application.
c)      Logical Components of the Road Warrior Application:
We did a thorough analysis of the Road Warrior problem domain by employing the suggested Logical Component Identification Process. We identified actors, actions, logical components, the role and responsibility statements of each component. This was an iterative process of at least 3—2 detailed and 1 fine.
Additionally, as an extension to this process, we created the following lists to enable us to finalize our architecture of the Road Warrior Application. We also used the following list as a reference to develop all our visual diagrams of the architecture—context, sequence diagrams, logical architecture.
Actors: Travelers, RW System
Systems: RW Application, Travel Systems & Partners ( Travel Agencies, SABRE, APOLLO), Social Media, Cloud DWH (within DMZ) Context Diagram
Interfaces: RW Web Application on Browser, RW Mobile Apps for Apple & Android (API GW APIs), Travel Systems (Bi-directional, Receiving Event Channel & Sending APIs) , Social Media ( RW>Social Media, APIs), Cloud DWH Interface ( Unidirectional, Cloud Ingestion Framework)
Workflows: Customer Sign up and Preference Setting, Customer Views and Updates Reservations, Customer Raises a Ticket, Travel Systems provide a Travel Event Update, Operational & Other Data Source Upload to Cloud DWH
Actions:
Traveller Actions
1.	Poll Email
2.	Filter/Whitelist
3.	Reservations CRUD
4.	Share Trip to Social Media
5.	Travel Usage Report
Road Warrior Actions
1.	Agency Interfacing (Receive Travel Update Events, Send Travel Updates)
2.	Dashboarding (Active Trips)=set of Reservations
3.	Travel Data Analytics
4.	Travel Systems Interfacing (SABRE,APOLLO)—Receive Updates
5.	Preferred Travel Agency (Chatbot)
Logical Components within RW App: Traveller, Traveller Preferences (include Travel Agencies), Trip, Reservations (Flight, Hotel, Cab); Traveller Email List; Travel Log (Log all the travel events for a traveller trip), Service Tickets
UI Views: User Registration, Preferences, Travel Reservations, Trip View (Dashboard), Travel Reports, Travel Email View, Ask for Help (Service Ticket)
Tables/Data Sources: Traveller, Traveller Preferences (include Travel Agencies), Trip, Reservations (Flight, Hotel, Cab); Traveller Email List; Travel Log (Log all the travel events for a traveller trip), Service Tickets.
Default Architecture Elements: UI/Apps, API GW, Cloud DWH, Service Mesh?, Multiple Tables/Data Sources, Queues, Cache, Load Balancer?
d)     Architecture Decisions Set for the Road Warrior Application:
 
We consider the following sets of architecture decisions as relevant to the Road Warrior application and initiative.
ADR1: Use ADR to record & audit all architecture decisions set.
ADR2: Adopt a distributed architecture with predominant microservices style.
ADR3: For real-time and responsiveness, adopt combination of event driven and request response
ADR4: For rich UIs, adopt micro frontends for UI Components.
ADR5: International & HA & Cost—Adopt Cloud Provider—AWS or Azure Setup?
ADR6: Adopt Cloud DWH for Travel Analytics Data—Modern Data Stack Setup
ADR7: ML Setup for Travel Trends, Churn Prediction,
 
 
 
 
7.    References
 
 
 
 
 
 
 
 
 
 


