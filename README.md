# IDPS
For my Final Year project, I created an Intrusion Detection and Prevention System using Python. The Operating System used was Linux. 




*This is My Final Year Report*

An Intrusion Detection System with the use of Machine 
Learning
24th April 2023
Final Year Project Report for the Degree of BSc Hons General Computer Science 

2 | P a g e
Abstract 
An intrusion detection system is a security technology designed to monitor network traffic 
and detect potential security threats. It is an essential component of network security, 
providing an additional layer of defence against cyber-attacks. This proposed project is 
intended to investigate the use of an intrusion detection system with a machine learning 
approach to monitor, gather data and effectively identify network breaches. Alongside 
developing an application to successfully identify security breaches would be the 
implementation of a honeypot and a firewall to make a network more secure. Furthermore,
the use of the honeypot is to give further insight in new vulnerabilities in an organisation as 
well as to help better define the security policy. 
Acknowledgments
I would like to thank predominantly Dr Ahmed Farhat and Dr Konstantin Kapinchev for their 
continued support and guidance throughout the creation of this project. Moreover, I would 
like to give a special thanks to my brother, my parents, and my friends for encouraging me 
through my studies and their ongoing support. Lastly, I would like to give a special thanks to 
the University of Greenwich with providing great opportunities to learn and better my 
education.
001090797
3 | P a g e
Definitions List
Intrusion Detection system: An Intrusion Detection System (IDS) is a type of security 
technology that monitors network traffic, system activity, or user behaviour for signs of 
unauthorised or malicious activity.
Intrusion Prevention System: An Intrusion Prevention System (IPS) is a type of security 
technology that detects any potential security breaches or attacks. Furthermore, the system 
takes active measures to prevent any attacks from succeeding. 
Machine Learning: Machine Learning (ML) is a subset of artificial intelligence (AI), it involves 
the development of algorithms and models that enable computers to learn from and make 
predictions or decisions based on data without explicit programming.
Packet Sniffer: A Packet sniffer, also known as a network analyser or protocol analyser, is a 
software or hardware tool used to capture and analyse network traffic in real-time.
Port Scanner: A Port scanner is a software tool or program that scans a computer or network 
for any open ports, these are communication endpoints used for network services.
Honeypot: A Honeypot is a decoy system or network that is intentionally designed to attract 
and detect attacks or intruders.
Firewall: A Firewall is a network security device or software that monitors and filters 
incoming and outgoing network traffic based on predefined rules or policies.
Packets: A Packet is a unit of data that is transmitted over a network. Furthermore, it is the 
smallest piece of data that can be sent over a network and typically consists of a header and 
a payload.
Header: A block of information that contains metadata or control information about the data 
being transmitted.
Payload: A Payload refers to the actual data or content that is carried within a data packet or 
message.
Threats: Threats refers to any potential dangers or risks that can harm or compromise the 
confidentiality, integrity, and availability (CIA Triad) of a system.
Vulnerabilities: This refers to the weakness or flaws in a computer system or network that 
can be exploited.
Exploits: This refers to techniques that a treat actor (attacker) can use to take advantage of a 
vulnerability.
Risks: A risk occurs when a system has a vulnerability which can be exploited.
Transmission Control Packet (TCP): TCP is a network protocol that is widely used and 
provides a reliable, connection-oriented communication between devices over a network. 
Furthermore, TCP operates at the transport layer of the open systems interconnection (OSI) 
model.
User Datagram Protocol (UDP): The UDP protocol also operates in the transport layer of the 
OSI model, however, unlike the characteristics TCP, UDP focuses more on real-time 
delivery of data at the sacrifice of reliability.
001090797
4 | P a g e
Internet Control Message Protocol (ICMP): The ICMP network protocol is used to send error 
messages and operational information about network conditions.
Internet Protocol version Four (IPv4): This is a Widley used network protocol for transmitting 
data over the internet and other IP-based networks. IPv4 provides the basic mechanisms for 
addressing and routing packets across networks, as well as for fragmenting and 
reassembling packets that are too large to be transmitted over the network in a single piece.
Internet Protocol version Six (IPv6): A network protocol that is designed to replace IPv4 
(Internet Protocol version 4) due to its limitations, such as the limited address space. IPv6 
provides a larger address space, improved security features, and other enhancements 
compared to IPv4.
Domain name system (DNS): This is a hierarchical and decentralised naming system for 
computer, services or other resources connected to the internet.
Address Resolution Ping (ARP): ARP is a protocol used in Local Area Networks (LANs) to 
map an IP address to a physical address (MAC). 
Ethernet (Ether): This is a term used to describe the transmission median for Ethernet 
networks.
Wi-Fi: A wireless networking technology that allows devices to connect and communicate 
with each other via radio waves.
Hypertext Transfer Protocol (HTTP): An application-layer protocol used for transmitting and 
receiving data over the internet
Hypertext Transfer Protocol Secure (HTTPS): An extension of HTTP that provides a secure 
communication over the internet.
Denial-of-Service (DoS) attack: A cyber attack that aims to disrupt a targeted computer 
system, network, or service by overwhelming it with an extensive amount of data thus 
exhausting it resources and causing the system to crash or become unstable. This includes 
a Neptune attack, Teardrop attack, Smurf attack, ICMP flood and UDP flood.
Unauthorised Access: This is when an attacker gains access to a system, network, or 
application without authorisation. Common types of Unauthorised access are Brute-force, 
social engineering, and privileged escalation.
Confidentiality: This principle is to ensure that sensitive data is only accessible to authorised
personnel.
Integrity: This principle focuses on maintaining the accuracy and consistency of data.
Availability: The is ensure that information and systems are accessible to authorised users 
when needed. 
001090797
5 | P a g e
Table of Contents
Contents
1. Literature Review .........................................................................................................................7
1.1 Introduction.................................................................................................................................7
1.2 Problem Domain ........................................................................................................................8
1.2.1 Background .........................................................................................................................8
1.2.2 Advancements in Intrusion Detection Systems .............................................................9
1.2.3 Similar studies...................................................................................................................10
1.3 Concluding Statement.............................................................................................................11
1. Methodology................................................................................................................................12
2.1 Use Case Diagram ..................................................................................................................12
2.2 Basic First Steps Waterfall .....................................................................................................12
2.3 Useful Python Libraries...........................................................................................................14
2.4 Project Functionality................................................................................................................15
2.5 Success Criteria of Project.....................................................................................................15
2.5.2 Functional Requirements ................................................................................................16
2.5.2 Non-Functional Requirements........................................................................................17
2.6 Legal and Ethical Considerations..........................................................................................17
2. Implementation ...........................................................................................................................19
3. Testing, Evaluation and Critical Analysis................................................................................27
4.1 Testing Table............................................................................................................................27
4.2 Test Fixes .............................................................................................................................30
4.3 Evaluation of Test Cases .......................................................................................................31
4.4 Evaluation of XGBoost algorithm ..........................................................................................32
4.5 The Evaluation of Data tested ...............................................................................................34
4.6 Critical Analysis of IDS ...........................................................................................................34
4. General Summary and Conclusions........................................................................................36
5.1 Summary of Project.................................................................................................................36
5.2 Limitations and Future Work ..................................................................................................36
5.3 Personal Reflection .................................................................................................................36
5. References ..................................................................................................................................38
6. Appendix......................................................................................................................................41
001090797
6 | P a g e
List of Figures 
Figure 1.Use Case Diagram ................................................................................................. 12
Figure 2. Basic Waterfall Diagram ........................................................................................ 14
Figure 3. Login GUI............................................................................................................... 19
Figure 4. Main GUI................................................................................................................ 19
Figure 5. Packet Sniffer GUI ................................................................................................. 20
Figure 6. Packet Sniffer CSV File save GUI ......................................................................... 20
Figure 7. Port Scanner GUI .................................................................................................. 21
Figure 8. Honeypot GUI ........................................................................................................ 21
Figure 9. Firewall GUI ........................................................................................................... 22
Figure 10. Intrusion detection GUI ........................................................................................ 22
Figure 11. CSV analyses upload GUI ................................................................................... 22
Figure 12. Packet Capture Code .......................................................................................... 23
Figure 13. CSV Upload Code ............................................................................................... 23
Figure 14. Empty Dataset Analyses Code ............................................................................ 23
Figure 15. DataFrame Filter code ......................................................................................... 24
Figure 16. Pre-processed data Code.................................................................................... 24
Figure 17. Pre-trained XGBoost classifier model Code ........................................................ 24
Figure 18. Attack identification.............................................................................................. 24
Figure 19. Enable Firewall Code........................................................................................... 25
Figure 20. Port Scanner Code .............................................................................................. 26
Figure 21. Test 3 Fix ............................................................................................................. 30
Figure 22. Test 3 fix displayed in GUI................................................................................... 30
Figure 23. Dictionaries .......................................................................................................... 31
Figure 24. Features............................................................................................................... 31
List of Tables 
Table 1. Testing Table .......................................................................................................... 27
Table 2. XGBoost Performance Table .................................................................................. 32
001090797
7 | P a g e
1. Literature Review 
1.1 Introduction 
This chapter will provide a general introduction in which an explanation of what an intrusion 
detection system is, how the implementation of machine learning can assist, why the 
information gathered may be beneficial and an understanding towards online security. 
With the increasing use of computer networks in various industries and daily life, network 
security has become a significant concern. Network security is defined as the “the process 
through which we can protect the digital information within the system and also during 
transmission” (Jenani, 2017). Furthermore, network security refers to the measures and 
techniques used to protect computer networks from various types of cyber-attacks (Aslan et 
al., 2023). It involves implementing a range of security measures, such as firewalls, intrusion 
detection systems, and encryption, to safeguard a network from any risks. With the increasing 
reliance on technology and the internet for conducting business and communication, network 
security has become more critical than ever before. Network breaches can result in a 
significant loss of data, financial losses, and reputational damage. Therefore, organizations 
must take network security seriously and implement effective measures to ensure the 
confidentiality, integrity, and availability of their network resources (Goodman & Rowland, 
2021).
Moreover, weak network security can lead to various threats that can have severe 
consequences for both individuals and organisations (Jiang, 2021). This is done through 
various methods of attacks such as unauthorised access, malware attacks, denial-of-service 
attacks, social engineering attacks, and data breaches. Data such as personally identifiable 
information (PII), personally health information (PHI), identity theft, financial fraud, login 
passwords, and disruption of organisational activities could be provided by such attacks. Such 
threats could seriously harm an organization's reputation and endanger the safety of its 
customers.
Gregory D. Podolak (2015) states that “the total number global of breaches from 2012 to 2013 
that resulted in the exposure of 522 million identities”. Considering that the numbers provided 
were over a decade ago and with the ever increase in network usage, the amount of leaked 
information has risen exponentially. In addition to this, the Thales Data Threat Report (2022) 
notes that, 53 percent of their respondents reported that they have experienced a security 
breach within the last 12 months. In addition to this, the leading cause of security threats that 
they reported were both malware attacks and ransomware attacks with a 55 percent and 47 
percent respectively.
In this era of constantly evolving cybersecurity threats, it is more important than ever to 
implement effective network security measures. This can be achieved through the use of 
firewalls, intrusion detection and prevention systems (IDPS), access controls, encryption, and 
regular vulnerability assessments, among other techniques. By prioritizing network security, 
organizations can protect their sensitive data, maintain business continuity, and safeguard 
against potential cyber threats as well as the risk associated with it. 
001090797
8 | P a g e
1.2 Problem Domain 
1.2.1 Background
Network security is a critical aspect of any organization's security posture. It involves the 
implementation of security measures to protect computer networks from unauthorized access, 
theft, damage, or disruption of network services. Network security is crucial because it ensures 
the confidentiality, integrity, and availability of organizational data. There are many avenues 
in which network security can be improved and the leakage of personal information can be 
lowered. One key component of network security can be the implementation of an intrusion 
detection system (IDS), this involves the monitoring and analysis of network traffic to detect 
any potential security breaches. Thakkar & Lohiya, (2022) further states that, the basic 
functionality of an IDS is to keep track of network activities, analysis of the gathered data, 
checking the system configurations for any existing vulnerabilities, identifying patters of 
different types of attacks, storing recognised patters in a database, and alerting the correct 
security personal if a security breach or recognition of an attack is found.
Additionally, there are two main types of intrusion detection systems, a host-based intrusion 
detection system (HIDS) and a network-based intrusion detection system (NIDS). Soniya &
Vigila (2016) explain that a HIDS is a software application that only scan the independent 
hosts machine on a network and not scan the entire network. This is accomplished by 
monitoring and analysing the network traffic that passes through the host and notify them if 
any malicious activity is detected. Furthermore, the author describe that a NIDS monitors all 
network traffic by placing the intrusion detection system along the network boundary. By doing 
so, the intrusion detection system “performs an analysis of passing traffic on the entire network 
and matches the traffic with the library of known attacks”.
Organisations employ intrusion detection systems as a critical component of their 
cybersecurity infrastructure to aid in identifying and thwarting potential threats. Furthermore, 
an IDS monitors network traffic and system activities for signs of suspicious activity. By 
implementing sophisticated algorithms, signature-based detection, and anomaly-based 
detection techniques, these systems provide real-time analysis and alerts to authorised 
personal. A notable real-world example would be the United States Department of Defence 
(DoD) and their deployment of an intrusion detection system to safeguard their extensive 
network infrastructure. Additionally, the DoD uses a Host Based Security System (HBSS), 
which is an IDS solution. This system has been beneficial to their security posture, as evidence 
from the 2018 report from the Defence Information System Agency (DISA), which highlighted 
that there was a 22% reduction in cyber incidents over a two-year period. 
However, while Intrusion Detection Systems play a vital role in enhancing network security, it 
is important to recognise that they are not fool proof solutions. IDSs primarily serve as an 
additional layer of protection, working in conjunction with other security measures to improve 
the overall security posture of an organisation. These systems may be susceptible to false 
positives, leading to unnecessary resource consumption, or false negatives, allowing 
malicious activities to go undetected. Furthermore, advanced adversaries may employ 
evasion techniques to bypass IDSs or exploit their inherent limitations. Consequently, 
organisations should view IDSs as a complementary component within a comprehensive 
cybersecurity strategy, employing a defence-in-depth approach that includes firewalls, antimalware software, encryption, and robust security policies. By integrating multiple security 
measures, organizations can achieve a higher level of protection and resilience against 
potential threats, rather than relying solely on an IDS to safeguard their networks and systems 
(Srinivas, Das & Kumar, 2019).
001090797
9 | P a g e
1.2.2 Advancements in Intrusion Detection Systems
Over the past few years, there have been several advancements in the field of intrusion 
detection systems designed to better detect and respond to potential security threats. With the 
implementation of various Machine Learning (ML) approaches, there has been a significant 
improvement in the identification of pattern recognition, adaptability, and flexibility (Mirlekar & 
Kanojia, 2022). Kilincer, Ertam & Sengur (2022) further state that, with the implementation of 
boosting algorithms such as EXtreme Gradient Boosting (XGBoost) can “increase speed and 
prediction performance”. This is particularly important as this can provide the analysis of raletime detection at a much more rapid rate thus allowing for a quicker response to the threat 
and minimising the impact of the security breach. Additionally, by incorporating different ML 
algorithms this can help to improve accuracy by reducing the number of false positive and 
false negative when identifying patterns and anomalies. Also, since machine learning has the 
capabilities to learn from past incidences thus this allows an improvement in the overall 
accuracy of the detection.
Moreover, another advancement in IDSs is the use of big data analytics (Fakar & Dogdu, 
2019). With the proliferation of connected devices and the Internet of Things (IoT), the amount 
of data generated by networks has increased significantly. IDSs that use big data analytics 
can process large volumes of data to identify patterns and anomalies that may indicate an 
intrusion. Big data analytics also enables IDSs to perform real-time monitoring of network 
traffic and provide immediate alerts for potential security breaches. Devarakonda et al., (2022) 
adds that, by incorporating a dataset such as “The Knowledge Discovery and Data Mining 
(KDD) Cup”, this can improve the predictive analysis, scalability and provide a historical 
analysis for the system. 
Another significant advancement in IDSs is the use of anomaly detection techniques. Anomaly 
detection is a technique that identifies patterns that deviate from the normal behaviour of the 
system or network. Furthermore, this detection method can be used to identify new attacks 
that are not covered by existing rule based IDSs. Such as the identification of zero-day attacks. 
This is particularly useful as it can provide information on newly discovered vulnerabilities in 
the system that have not yet been patched (Falcao et al., 2019). Moreover, anomaly detection 
techniques can be used in combination with ML algorithms to detect complex and targeted 
attacks (Radivilova et al., 2020). This can be accomplished through the use various methods 
such as supervised learning, unsupervised learning and a hybrid learning method. Supervised 
learning techniques are used to train classifiers with labelled data. Elthanbouly et al. (2020) 
states that, “The training and testing data used in these techniques should be assigned to a 
correct label for both normal and anomalous data instances”. Algorithms such as a Decision 
tree, Support vector machine and neural network are examples of supervised learning. On the 
other hand, unsupervised learning does not require ladled datasets. However, they are 
dependent on “discovering and analysing the structure of the input fields”. Common examples 
of unsupervised learning algorithms would include recurrent neural networks, one-class 
support vector machines and genetic algorithms. Alternatively, the implementation of a hybrid 
algorithm would provide the best result. A hybrid algorithm is the use of several machine 
learning techniques which would in turn perform different tasks. Furthermore, the hybrid 
system consists of creating two components. The outcome from each component “could be 
intermediary result that would be passed to another component”. This allows for the best 
outcome from each technique to overcome limitations from each individual algorithm. 
In addition to the above-mentioned advancements, IDSs have also been improved by the use 
of cloud-based architectures, which allow for the scalability and flexibility necessary to handle 
001090797
10 | P a g e
the growing volume of network traffic (Devi, Shitharth and Jabbar, 2020). Furthermore, the 
use of cloud computing, can provide multiple benefits to an organization. Benefits such as the 
providing access to global threat intelligence, this is particularly useful as the collection of data 
and insights of security threats and vulnerabilities are gathered and updated in real-time. This 
is particularly useful as an IDS that is deployed in the cloud has the potential to leverage this 
information and update, accordingly, thus enhancing the overall effectiveness of the security. 
In addition to the data collected, the implementation of machine learning or deep learning 
algorithms can leverage the data collected to analyse the large amounts of information and 
identify patterns of suspicious behaviour more precisely, thus reducing the number of false 
positives and false negatives. Devi, Shitharth and Jabbar (2020) further state, with cloud 
computing being centralised, this allows for the cost of security to be lowered. However, Chang 
et al., 2022 notes that the use of cloud-based architectures may be vulnerable to a variety of 
different risks. These include the malware injection (Cross-Site Scripting and SQL injection), 
data stealing and flooding attacks. Nevertheless, by ensuring that the correct measure, 
configurations, and constant management the risk can be lowered (Patel et al., 2013)
In conclusion, the advancements in IDSs have greatly improved their ability to detect and 
prevent security breaches. The use of ML and AI algorithms, big data analytics, anomaly 
detection techniques, and cloud-based architectures has made IDSs more effective and 
efficient in protecting networks from cyber threats. With the continued evolution of technology, 
we can expect even more exciting advancements in field of intrusion detection systems in the 
future.
1.2.3 Similar studies 
Wahal, Choudhury & Arora (2018) describes that the use of an intrusion detection system is 
designed to monitor network traffic and identify potential attacks or anomalies. Othman, 
Zahary & Nabeel (2018) further expands of the topic on intrusion detection systems and 
classify several types of IDSs based on their deployment locations and the detection 
techniques. The first type is a Host-Based IDS (HIDS), these detection systems are installed 
on an individual machine and monitors activity for the host. Next would be the implementation 
of a Network-Based IDS (NIDS), this is used to analyse network traffic to detect suspicious 
behaviour. Moreover, a combination of both a HIDS and a NIDS is called a Hybrid IDS. This 
takes the capabilities of both systems and combines them to produce a more comprehensive 
security solution. Othman, Zahary & Nabeel (2018) note that, the use of a signature-based or 
anomaly-based techniques can be incorporated in the previously mentioned IDSs to better the 
capabilities of the detection system. Kumar & Sangwan (2012) explains that a signature-based 
intrusion detection system works by examining network traffic for known patterns and 
signatures that are indictive of specific types of attacks. The signatures can be based of 
characteristics of an attack. This is accomplished as the IDS compare the network traffic with 
a database of know signatures and then generates an attack. On the other hand, Hajj et al., 
(2021) provides an explanation on the use of anomaly-based intrusion detection systems and 
how they are used to monitor network traffic and establishing a baseline of normal behaviour.
The use of machine learning algorithms in intrusion detection systems has become 
increasingly popular due to the ability to handle large amounts of data and detect sophisticated 
attacks. Kilincer, Ertam & Sengur (2022) explores various machine learning algorithms, 
including decision trees, artificial neural networks and boosting algorithms. Furthermore, the 
study found that ML algorithms could effectively and efficiently identify numerous attacks such 
as, Denial of Service (DoS), probing, and remote and local attacks. In addition to this, the 
study further noted that machine learning algorithms showed a better performance compared 
001090797
11 | P a g e
to standards signature-based methods. Moreover, when conducting their study, the authors 
found that the use of the eXtreme Gradient Boosting algorithm (XGBoost) outperformed other 
machine learning algorithms in terms of speed and accuracy for detecting cyber-attacks in a 
network-based intrusion detection system.
The report also contained useful information with regards to the use of datasets used for 
training and evaluating machine learning algorithms in various domains. Kilincer, Ertam &
Sengur (2022), use the KDD99 dataset, this dataset is particularly useful as it contains a large 
amount of network traffic data and a diverse number of cyber-attacks. The reason the authors 
used this dataset is due to the reason that it allows the machine learning algorithms to learn 
form a wide range of scenarios and accurately detect various attacks. Gurung, Ghose & 
Subedi (2019) further note that, the use of the KDD99 dataset is used as a common 
benchmark dataset that is well-known and widely used by various researchers, thus allowing 
to compare and ensure the reliability of the IDS.
1.3 Concluding Statement
In conclusion, the field of network security and the utilisation of an intrusion detection system 
to facilitate and secure a network, is a field that has been observed and explored previously. 
However, as cyber threats continue to grow in complexity and scale, the importance if a robust 
and efficient intrusion detection system cannot be overstated. Through this literature review 
we have explored the various aspects of an IDS, including the different types, the 
advancements in the field, the challenges present and the utilisation of machine learning 
techniques for effective threat detection. Furthermore, intrusion detection systems are an 
important component in the network infrastructure. As the cyber landscape continues to evolve 
it is imperative to continue advancing and adapting and IDS through ongoing research and 
the integration of emerging technologies, such as employing the application via cloud 
architecture. By doing so, the development in a sophisticated and adaptive system will be vital 
in maintaining a confidential, integral, and available network. 
001090797
12 | P a g e
1. Methodology
2.1 Use Case Diagram 
When launching the application, the user is faced with a login page (as shown in Figure 1), if 
the login credentials are incorrect (for instance the username or password are invalid) an error 
message will appear. However, if the user enters the correct credentials, they will have access 
to the main graphical user interface. From there the user is able to select a verity of features. 
This could be the use of a Packet Sniffer, a Port Scanner, a Honeypot, or a Firewall. If the 
client was to choose the Packet Sniffer, they would be able to gather the relevant information 
and save it to a pcap file. The user would then be able to run the information gather in a 
Machine Learning Algorithm to detect any anomalies in the data. This can then provide 
information on any suspicious activity within the network. However, if the user chooses the 
Port Scanner, they are then shown the relevant information regarding the ports on which the 
host machine is listening on, this can show both TCP and UDP ports. Likewise, if the user was 
to choose the Honeypot feature, this will give the opportunity to launch a vulnerable decoy 
system on different ports. The information gathered from the honeypot will provide the client 
with valuable information concerning the types of vulnerabilities and types of attacks that may 
be performed on the network. Similarly, if a client were to choose the Firewall feature, this will 
give the user the ability to launch a firewall on different ports to limit the network traffic.
Figure 1.Use Case Diagram
2.2 Basic First Steps Waterfall 
The Waterfall method (Figure 2) illustrates the lifecycle of the project’s creation. The diagram 
shows the initial steps of brainstorming ideas to the final product of a functional intrusion 
detection system with the implementation of machine learning. Furthermore, the illustration 
provides details on the projects development and how to reach the end goal.
001090797
13 | P a g e
• Brainstorm Ideas – During the brainstorming phase, ideas should be formed with 
regards to the reason for the application, how the program is going to be constructed 
and id there are any potential software’s to use. Furthermore, this phase should 
research on current implementation of the program and to find gaps. Once this initial 
phase is complete, the production of the program can begin. 
• Allocate Criteria – This stage of the project is used to determine the success criteria of 
the final product. This is a vital step in the production any application as it highlights 
the primary criteria that the product must accomplish.
• Create plan and begin design – Once a foundation has been created, ideas have been 
circulated and the success criteria is established, the next step is to begin sketching 
out a Graphical User Interface (GUI) as well as creating logical connections between 
the different features and other utilities.
• Create initial GUI – Once everything has been planned the construction of the initial 
GUI can begin (coding begins). This phase allows the ideas created to be put in place 
and the different layers to become finer tuned. 
• Develop code – This phase is where the research and development of different python 
libraries are introduced into the production of the program to better the efficiency and 
effectiveness.
• Creation of other functionalities/GUI’s – Once the previous two phases are complete, 
the next step is to begin on working on different functionalities that the intrusion 
detection system can implement to fill the success criteria set in the beginning. This 
includes the development of the Firewall, Honeypot, Packet Sniffer and Port Scanner.
• Test Features – This phase consists of testing each feature individually. This allows to 
determine if each component of the program is producing the information that is 
necessary to the user. Furthermore, this allows to troubleshoot each part and better 
the final product. Examples of this would be to ensure that the Packet Sniffer collects 
data packets that are transmitted over the network and saves them to a pcap file. The 
port scanner would need to be able to display the TCP and UDP ports that are open. 
The Honeypot should be able to be deployed on a singular or multiple ports and display 
the information for the user. Finally, the Firewall should be able to be deployed on a 
singular or multiple ports and limit the network traffic.
• Creation of ML algorithm – Whilst creating and testing of the other feature is underway, 
the process in which the machine learning (ML) algorithm is being constructed. This 
reason for this is to ensure that the information that is gathered coincides to that of the 
dataset used to train the ML.
• Train ML – Once the code is complete, the next phase is to train to train the algorithm 
with reliable datasets to ensure an accurate and precise algorithm. 
• Collection of information – This step involves collecting information from the IDS and 
test the ML.
• Test IDS as a Whole – Once everything is complete and fine-tuned, the entire IDS is 
tested to ensure the information gathered, the detection is accurate, and the final 
product fulfils the success criteria.
001090797
14 | P a g e
Figure 2. Basic Waterfall Diagram
2.3 Useful Python Libraries
Creating an intrusion detection system (IDS) involves analysing network traffic, system logs, 
and other data to detect potential security threats. Python, as a versatile object-oriented
programming language, offers several useful libraries that can be utilized in building an IDS. 
Some of these libraries include:
Scapy: Scapy is a powerful packet manipulation library that allows capturing, analysing, and 
forging network packets. It provides the ability to capture network traffic, extract relevant data 
from packets, analyse packet payloads, headers, and protocols (Wahal, Choudhury & Arora, 
2018). Furthermore, Scapy is widely used in the development of IDS’s for packet inspection, 
anomaly detection and intrusion detection. 
Socket: The Socket library in Python is a built-in module that provides a way to create, interact 
with, and manage network sockets, which are the endpoints for sending and receiving data 
over a network. Sockets allow for communication between different processes running on the 
same machine or across different machines connected to a network (Singh, 2019).
Threading: The Threading library in Python is a built-in module that provides a way to create 
and manage threads for concurrent execution within a single process. Threads are lightweight 
and can run in parallel, allowing for concurrent execution of multiple tasks in a program, which 
can improve performance and responsiveness.
Pandas: The “Python Data Analysis Library” (Pandas), library is a popular open-source data 
manipulation and analysis library for Python. It provides data structures and functions needed 
to work with structured and tabular data, making it a powerful tool for data analysis, data 
cleaning, data transformation, and data visualization tasks. Furthermore, the primary use of 
this library is to intake data and output Python objects with columns and rows named data 
frames. This allows the interpretation and manipulation of data to be more manageable.
Tkinter: The Tkinter library is a standard Python library for creating graphical user interfaces 
(GUIs). It provides a set of tools and functions for creating windows, dialogs, buttons, labels, 
text boxes, and other GUI elements, allowing you to create interactive applications with a 
graphical interface (Amos, 2020).
001090797
15 | P a g e
eXtreme Gradient Boosting (XGBoost): XGBoost is a popular library in Python used to 
increase speed and predictive performance. It is an optimised implementation of the gradient 
boosting machine learning algorithm designed for high performance and efficiency. Kilincer, 
Ertam & Sengur (2022) notes that, the XGBoost algorithm “includes several settings that 
reduce over-filtering and improve overall performance”. This provides a more accurate 
feasible and efficient algorithm. Furthermore, the use of the XGBoost algorithm in the project 
is used as a classifier to predict the type of network attack based on the given features. The 
code demonstrates how to pre-process the input data, load a pre-trained XGBoost model, and 
make predictions using the model.
2.4 Project Functionality 
Similarly, to the project proposal, the project shall be a Python application that will identify 
possible threats that the network may face as well as help classify the types of vulnerabilities 
found within the network. Certain metrics must be met in order for the project to be deemed 
successful such as, providing the user with options to scan the network for information, provide 
a security measure that will help prevent malicious activity on the network and an efficient and 
accurate algorithm to detect any anomalies. An example of this would be to scan the network
with the use of a packet sniffer for a specified time period and gather as much data as possible, 
once complete the next step is to use the machine learning algorithm to analyse the data and 
detect any suspicious activity. If there seems to be any irregularities on the network the user 
will then be alerted on the irregularity and necessary action can begin. Furthermore, if the user 
wishes to gather further information on a port about the types of attacks used against the 
system and evaluate the current vulnerabilities on the network, they can launch either a firewall 
or honeypot on the chosen ports. This is accomplished by allowing the user to be able to 
identify the open ports on the machine with the use of a port scanner.
2.5 Success Criteria of Project 
For the software to be deemed successful, it will have to meet certain criteria known as 
success criteria. This will be based on an array of factors such as what the program aims to 
achieve, the level of depth, time constraints as well as other measurements put in place.
• Time
The first success criteria the project will be based on is the is the time taken to complete 
a fully functioning program. The deadline set by myself for this was the 15th of April 2023. 
This deadline was specifically chosen as this would determine if the application would 
either pass or fail.
• Fit for purpose
This criterion is set to ensure that the application is both user-friendly as well as ensuring 
that the final product is to increase the online security of a network.
• Fits Functional Requirements 
Functional requirements are the features and capabilities that a software system or 
application must possess to meet the needs of its users and fulfil its intended purpose. 
They describe what the software is supposed to do and how it should behave in terms of 
its functionalities. Furthermore, functional requirements are typically documented during 
001090797
16 | P a g e
the requirements gathering and analysis phase of software development, and they serve 
as a foundation for designing, implementing, and testing the software system
• Fits Non-functional Requirements
Non-functional requirements are the characteristics or qualities that a software system or 
application must possess to meet certain performance, reliability, security, and usability 
standards. They describe how well the software should do what it does, rather than what 
it does. Non-functional requirements are typically documented alongside functional 
requirements during the requirements gathering and analysis phase of software 
development, and they help to ensure that the software system meets the desired quality 
attributes.
2.5.2 Functional Requirements 
Login Functionality: The system should allow users to enter their username and password in 
the login GUI. The system should check the entered credentials against a predefined 
username and password (e.g., "admin" and "password"). If the credentials match, the system 
should allow the user to log in and proceed to the IDS GUI. Otherwise, an error message 
should be displayed indicating that the username or password is invalid.
Firewall Functionality: The system should provide a "Firewall" button in the IDS GUI. When 
clicked, it should open the firewall interface. Furthermore, the functionality of the firewall 
should be able to filter incoming and outgoing traffic as well as allow the user to specify which 
ports they would like to launch the firewall on.
Honeypot Functionality: The system should provide a "Honeypot" button in the IDS GUI. When 
clicked, it should open a new GUI that allows the user to specify which ports to deploy the 
system. Additionally, the Honeypot should be able to save the data collected.
Packet Sniffer Functionality: The system should provide a "Packet Sniffer" button in the IDS 
GUI. When clicked, it should trigger a new interface in which the user is able to start and stop 
analysing the network that they are connected to. Moreover, the user should be able to save 
the information collected.
Port Scanner Functionality: The system should provide a "Port Scanner" button in the IDS 
GUI. When clicked, it should the user should have the ability to scan the open TCP and UDP 
ports that the machine is listing to. The information should also be presented to the user as it 
will help to identify which ports to launch the honeypot and firewall.
Machine Learning Functionality: The program should provide a “Machine Learning Algorithm. 
This will allow the user to analyse the collected data from the packet sniffer at a quicker rate 
as well as more accurately. Also, the user will be able to upload and analyse a csv. Once the 
analyses is complete the algorithm will detect an anomalies in the data and highlight it for the 
user to easily identify the type of attack. 
User Interface: The system should provide a user-friendly graphical user interface (GUI) using 
the tkinter library, with appropriate labels, entry widgets, and buttons for inputting credentials 
and triggering the different functionalities of the IDS.
Error Handling: The system should handle errors appropriately, such as displaying error 
messages for invalid credentials or any other errors that may occur during the execution of 
the external scripts.
001090797
17 | P a g e
Security: The system should ensure proper security measures, such as validating and 
sanitizing user input to prevent code injection attacks, and using safer alternatives (e.g., 
subprocess module) for executing external scripts to mitigate potential security risks.
2.5.2 Non-Functional Requirements 
Performance: The system should be responsive and provide efficient performance in terms of 
login processing, executing external scripts, and handling GUI interactions. The system should 
avoid any unnecessary delays or lags that may affect the user experience.
Reliability: The system should be reliable and available for use whenever needed. It should 
handle errors gracefully and provide appropriate error messages to users in case of failures, 
such as invalid credentials or errors during the execution of external scripts.
Scalability: The system should be designed in a scalable manner, allowing for future 
enhancements and additions of new functionalities. It should be easy to extend or modify the 
system without disrupting the existing functionalities.
Maintainability: The system should be easy to maintain and update, with clean and modular 
code that follows coding best practices. It should be well-documented, making it easier for 
developers to understand and modify the code as needed in the future.
Security: The system should follow best practices for security, such as properly validating and 
sanitizing user input to prevent code injection attacks and using safer alternatives. The system 
should also protect sensitive information, such as usernames and passwords, and ensure 
secure communication between components.
Usability: The system should be user-friendly and easy to use, with clear and intuitive user 
interfaces that allow users to easily input credentials, interact with buttons, and understand 
the system's functionalities. It should also provide appropriate feedback and error messages 
to guide users in case of any issues.
Compatibility: The system should be compatible with the targeted environment, including the 
operating system, Python version, and any dependencies or external scripts used. It should 
be thoroughly tested in the intended environment to ensure proper functioning.
Portability: The system should be designed to be portable, allowing for easy deployment on 
different systems or platforms. It should not have hard-coded dependencies or system-specific 
configurations that may hinder its portability.
2.6 Legal and Ethical Considerations 
Building an intrusion detection system involves several legal and ethical considerations. These 
considerations may vary depending on your location, jurisdiction, and the specific use case of 
the IDS. Here are some general legal and ethical considerations to keep in mind:
Compliance with Laws and Regulations: This ensure that when creating an IDS, complies with 
all applicable laws, regulations, and industry standards related to privacy, data protection, and 
cybersecurity. This may include local, national, and international laws and regulations, such 
as the General Data Protection Regulation (GDPR) and the Computer Fraud and Abuse Act 
(CFAA), among others (Overill, 2004).
Data Privacy and Consent: It is vital to consider the privacy implications of collecting and 
analysing network traffic data. Furthermore, ensuring appropriate consent or legal basis for 
001090797
18 | P a g e
processing any personal data and handle the data in accordance with applicable privacy laws 
and regulations. In addition to this, transparency about what data is collect and how it is used
is necessary (Parker, Pine & Ernst, 2018).
Ethical Use of Data: Consider the ethical implications of using data collected by the IDS. Use 
the data only for legitimate and ethical purposes and avoid any unethical or malicious use of 
the data, such as unauthorized monitoring, data theft, or data manipulation (Atlam & Willls, 
2019).
User Notification and Consent: Clearly inform users or stakeholders who may be subject to 
monitoring by the application. Moreover, it is important to obtain proper consent or provide 
appropriate notice before implementing an IDS in any network or system and respect the 
privacy rights and expectations of users.
Security of the IDS: Ensure that your IDS is built and configured securely to protect against 
unauthorized access, tampering, or misuse. Implement appropriate security controls, such as 
access controls, authentication, encryption, and monitoring, to safeguard the integrity, 
confidentiality, and availability of the program and the data collected (Lundin & Jonsson, 
2002).
Liability and Legal Responsibility: Understand the legal implications and potential liabilities 
associated with building and deploying an IDS. Also, awareness of the risks and 
responsibilities involved and take appropriate measures to minimize legal and financial 
liabilities, such as obtaining legal advice, having proper insurance coverage, and complying 
with legal requirements.
It is important to consult with legal and ethical experts and follow applicable laws, regulations, 
and industry standards when building your own IDS. Compliance with legal and ethical 
considerations is essential to ensure that the IDS is used responsibly, ethically, and lawfully, 
and to protect the rights and privacy of all stakeholders involved.
001090797
19 | P a g e
2. Implementation
Login GUI
When a user begins the application, they are met with a Login page. This is done to create 
security around the application and ensure that only authorised personal are accessing the 
program. If the user enters the correct credentials they will be directed to the main GUI. 
Figure 3. Login GUI
Main GUI 
The main interface (as seen in Figure) was constructed with the intention for being simplistic 
and easy to navigate for the user. Furthermore, the application is set to a constant colour 
scheme. The only with the page that the users will be able to have on the main interface would 
be buttons. The buttons are used to guide the user to specific features which include the 
packet sniffer, port scanner, honeypot, and firewall. Once the user decides which feature, they 
would like to access, a new interface will open in which they can use the specified feature.
Figure 4. Main GUI
Secondary GUI’s
The secondary graphical user interfaces were built to convey the information gathered in a 
simplistic manner as well as provide the handler with a user-friendly experience. Through 
these different interfaces, the user can gather relevant information by using the packet sniffer 
or port scanner, as well as to launch either a honeypot or firewall on specific ports. 
001090797
20 | P a g e
Packet Sniffer 
Once the user enters this interface by clicking the “Packet sniffer” button, they can capture 
data packets on a network. Once the user initiates the program by clicking the start button, 
they can capture data packets in real time on the network. Once the user has completed the 
packet sniff or is satisfied with the amount of data captured, they are then able to click the 
save button. This will prompt the user with an option to save this captured data as a CSV file 
on the system. 
Figure 5. Packet Sniffer GUI
Figure 6. Packet Sniffer CSV File save GUI
001090797
21 | P a g e
Port Scanner
If the user chooses to enter this feature, they are presented with an interface that will display 
the TCP and UDP port for which the machine is listening on. This is accomplished by clicking 
the scan button.
Figure 7. Port Scanner GUI
Honeypot
If the user were to access this feature, they will be directed to an interface on which they will 
be allowed to launch the honeypot on either one specific port or multiple ports. Furthermore, 
the information is updated in real-time to a csv file. This allows the user to view the date and 
time of the attack, the port from which the attack happened, the IP address and the type of 
attack. 
Figure 8. Honeypot GUI
Firewall 
For the Firewall, if the user were to click on the firewall option, they will then be directed to the 
firewall interface. From here the user enter the ports in which they wish to launch the firewall 
by entering the text box. The user will then be notified in the terminal that the firewall is active 
on the specified ports. 
001090797
22 | P a g e
Figure 9. Firewall GUI
Alert System
Lastly, once the user has captured the network packets from the use of the packet sniffer and 
saves the csv file, they are then able to access the “Network Intrusion Detection” interface. 
From here the user can click on the “Analsye CSV” button. From here, the user is able to 
upload the file and begin analyses of the data. If there are any anomolies, the text will be 
highlighted yellow along with the attack type, however is the data seems normal, the text will 
show a non-highlighted text stated as “normal”
Figure 10. Intrusion detection GUI
Figure 11. CSV analyses upload GUI
Initialising a connection to the network and begin the scan:
As specified in the design section, the packet sniffer in initialised and begins to scan the 
network on which the host is on. Once the user clicks the “Packet Sniffer”, they then have 
access to the sniffers GUI, thus allowing them to start a network scan and save the data. This 
is accomplished with the following code:
001090797
23 | P a g e
Figure 12. Packet Capture Code
In this method, an instance of the ‘AsyncSniffer’ class from the Scapy library is created with 
the following parameters: 
• “prn=self.process_packet”: The ‘prn’ parameter specifies the callback function 
(‘process_packet’) that will be called to capture each packet.
• “store=False”: This parameter tells the sniffer not to store the captured packets in 
memory, as the packets are being processed by the callback function.
• “self.sniffer.start”: This method starts the asynchronous packet capturing process in 
the background.
Analyses of data using the XGBoost algorithm.
The following code explains how the XGBoost algorithm can analyse a csv file and examine 
the data captured from the packet sniffer.
Figure 13. CSV Upload Code
• “file-path = filedialog.askopenfilename(filetypes=[(“CSV Files”, “*.csv”)])”: The 
following part of the code opens a file dialog, this allows the user to select a CSV file.
• “df = pd.read_csv(file_path)”: This code takes the chosen CSV file and it is then read 
into a pandas DataFrame.
Figure 14. Empty Dataset Analyses Code
The code seen in the above figure checks if the DataFrame is empty. If it is, a message will 
appear to the user to enter a valid dataset. 
001090797
24 | P a g e
Figure 15. DataFrame Filter code
This part of the code filters the DataFrame to keep only the columns listed in ‘self.cols’.
Figure 16. Pre-processed data Code
As seen in the above code snippet (Figure 16):
‘X_processed = self.preprocess_data(df)’: The data is pre-processed using this method, which 
encodes categorical columns and imputes missing numerical values.
Figure 17. Pre-trained XGBoost classifier model Code
The code seen above (Figure 17), is the pre-trained algorithm classifier model. This is then 
loaded with a CSV file and then used to predict the type of network traffic for each entry in the 
pre-processed data. 
Once complete, the “preds” variable contains the prediction for each entry in the CSV file. The 
results are then displayed in the GUI (Figure 10) and the detected attack types are highlighted. 
Honeypot attack identification:
The following code as seen in Figure 18 is a function used to identify SQL injections 
or Cross-Site Scripting (XSS) attacks based on certain patterns. 
“types_sql_injection”: This is a list containing regular expression patterns that frequent 
common SQL injection signatures.
“types_xss”: This is a list containing common expression patters that represent 
frequent XSS attack signatures.
Figure 18. Attack identification
001090797
25 | P a g e
Firewall Code Functionality:
The code snippet seen Figure 19 is responsible for processing the user input, converting it 
into a list of integers representing port numbers, and creating the corresponding iptables rules 
to block incoming traffic on those ports.
“rules = ["sudo iptables -A INPUT -p tcp --dport {} -j DROP".format(port) for port in ports]”: This 
part of the code creates the list of iptables rules to block incoming traffic on the specified ports.
Figure 19. Enable Firewall Code
Port Scanner:
In the code snippet, as seen in Figure 20, cans all available TCP and UDP ports on the host 
machine. This was implemented in order to help the user identify which ports to deploy the 
honeypot or firewall. 
“for protocol in ('tcp', 'udp')”: This loop iterates over a tuple containing two strings, ‘tcp’ and 
‘udp’. This is used to loop over each port and check if they are open.
“for port in range(1, 65536)”: This inner iterates over all possible port numbers from 1 to 65535. 
“sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM” if protocol == 'tcp' else 
“socket.SOCK_DGRAM)”: This part of the code creates a socket object using the 
“socket.socket()” function. The first argument, “socket.AF_INET”, specifies that the socket will 
use IPv4. 
The second argument selects the socket type based on the current protocol value. If protocol 
is 'tcp', the socket type is set to “socket.SOCK_STREAM”. If protocol is 'udp', the socket type 
is set to “socket.SOCK_DGRAM”.
001090797
26 | P a g e
Figure 20. Port Scanner Code
001090797
27 | P a g e
3. Testing, Evaluation and Critical Analysis 
This section will demonstrate how the program works as it is intended to. Furthermore, it will 
contain the test ran on the application as well as the reasoning behind why it is crucial to 
execute the test as well as a summary of the tests conducted. In addition to this, critical 
evaluation will be implemented along with the tests, this will highlight the strength and 
weaknesses of the application.
Also, this section will provide a testing table. The testing table will be a form of a black box 
test. Black box testing is a software testing technique that involves examining the functionality 
of a software application without considering its internal structures or workings. The objective 
of black box testing is to ensure that the software functions correctly from the user's 
perspective, regardless of how it is implemented internally. Furthermore, this method of testing 
is important because it can help identify defects or vulnerabilities that may not be evident 
through other types of testing. By simulating real-world usage scenarios and testing the 
software in a controlled environment, black box testing can provide assurance that the 
software will perform as expected in the hands of end-users. Furthermore, it can help ensure 
that the software meets the required specifications and regulatory requirements (Nidhra & 
Dondeti, 2012).
4.1 Testing Table
A testing table, also known as a test plan, is an important tool for testing an Intrusion Detection 
System (IDS). The primary purpose of an IDS is to detect and alert on potential security threats 
or attacks against a system or network. A testing table provides a structured approach to 
testing an IDS by defining the specific tests that will be performed and the expected outcomes 
of those tests. This allows for a systematic and repeatable testing process that can help 
identify any gaps or weaknesses in the IDS.
By using a testing table, you can ensure that the application is tested thoroughly and 
comprehensively, covering various scenarios and attack vectors as well as basic functionality. 
It can also help ensure the appropriate steps are taken when trying to troubleshoot the 
program and fix any error that may occur. Furthermore, well-designed testing table can help 
improve the overall effectiveness and reliability of the IDS, which is crucial for maintaining the 
security and integrity of your system or network. Additionally, having a documented testing 
plan can also be useful for compliance and auditing purposes.
Table 1. Testing Table
Test Case 
Number
Test 
Objective
Test Steps Expected 
Outcome
Actual 
Outcome
Pass/Fail
1 Verify IDS 
detects 
attacks
1. Use a 
dataset with 
known 
attacks.
The IDS can 
Correctly 
identify the 
different 
attacks from 
the KDD99 
dataset
The Algorithm 
was able to 
analyse the 
data and 
identify the 
attacks 
correctly 
Pass
001090797
28 | P a g e
2 Verify IDS 
detects 
normal 
network traffic
1. Analyse a 
dataset with 
normal 
traffic.
The IDS can 
analyse the 
captured data 
and identify if 
the network 
traffic is 
considered 
“normal” 
The IDS can
identify 
captured data 
and 
determine if it 
is “normal” 
traffic
Pass
3 Test IDS with 
empty dataset
1. Analyse 
an empty 
dataset.
The system 
should handle 
the empty 
dataset 
without errors 
and return an 
appropriate 
message or 
empty result
The IDS is 
unable to 
analyse an 
empty dataset 
and returns 
an error 
message in 
the terminal.
Fail
4 Verify IDS can
analyse the 
data captured 
from the 
Packet Sniffer
1. Configure 
IDS to be 
able to read 
the captured
data from the 
Packet 
Sniffer.
2. Correctly 
Identify data.
IDS can 
analyse the 
data and can 
correctly 
identify.
The IDS can 
analyse the 
data from the 
Packet Sniffer 
and is able to 
correctly 
identify the 
data.
Pass
5 Verify IDS 
logs all 
detected 
events
1. Perform 
various 
attacks on 
the test 
system.
2. Check IDS 
logs for all 
detected 
events.
IDS logs all 
detected 
events.
IDS can log 
all events.
Pass
6 Verify 
Honeypot 
functionality
1. Deploy a 
honeypot on 
the test 
system.
2. Monitor 
the honeypot 
logs for 
attacker 
activity.
Honeypot 
generates 
logs of 
attacker 
activity.
Start by 
enabling the 
honeypot on 
an open port. 
Once 
complete, 
launch an 
attack on the 
system and 
see if the 
honeypot 
identifies the 
attack and 
save the 
information to 
a CSV File.
Pass
001090797
29 | P a g e
7 Verify Firewall 
functionality
1. Configure 
the firewall to 
block traffic 
to a specific 
port or IP 
address.
2. Attempt to 
access the 
blocked 
resource 
from a 
remote 
system.
3. Check 
firewall logs 
for blocked 
traffic.
Firewall 
blocks/filters
traffic to the 
specified 
resource.
Once a port is 
chosen and 
the Firewall is 
enabled. 
Simply 
running an 
Nmap on the 
port should 
indicate if the 
firewall is 
enabled on 
the system. If 
it shows 
“Filtered” then 
it works.
Pass
8 Verify Port 
Scanner 
functionality
1. Run a port 
scanner 
against the 
test system.
2. Check the 
port scanner 
logs for open 
ports.
Port scanner 
detects all 
open ports on 
the test 
system.
Port scanner 
shows all 
TCP and UDP 
ports that are 
open.
Pass
9 Verify Packet
Sniffer 
functionality
1. Capture 
network 
traffic on the 
test system 
using a 
packet 
sniffer and 
save to a 
CSV File.
2. Packet 
Sniffer able 
to collect 
similar data 
to that of the 
KDD99 
dataset
Packet sniffer 
captures all 
network 
traffic.
The Packet 
Sniffer 
captures all 
network traffic
and can save 
to a CSV File.
Fail 
10 Functionality 
of the GUIs
1. Run the 
application 
and test if 
the GUIs are 
functional 
The GUIs are 
functional with 
clear 
instruction 
where 
needed.
All the 
different GUIs 
are functional 
and have 
clear 
instructions 
where 
needed 
Pass
001090797
30 | P a g e
4.2 Test Fixes 
Test number 3: When entering an empty dataset, the programs returns the following error, 
“ValueError: Found array with 0 sample(s) (shape=(0, 3)) while a minimum of 1 is required by 
SimpleImputer.” The code didn't handle the case when an empty dataset is entered because 
it didn't check if the DataFrame ‘df’ is empty or not. To fix this issue the come seen in the figure 
below will allow to check if the data is empty and handle it accordingly.
Figure 21. Test 3 Fix
Figure 22. Test 3 fix displayed in GUI
001090797
31 | P a g e
Test number 9: When capturing network traffic, the original version of the packet sniffer was 
only able to collect basic information. This was an issue as the ML algorithm was unable to 
analyse the data and produce an output. However, this was fixed by adding a dictionary for 
the TCP and UDP services, as well as a features list as seen in Figure 23 and Figure 24
respectively.
Figure 23. Dictionaries
Figure 24. Features
4.3 Evaluation of Test Cases
The test cases in the above testing table were chosen to cover a range of security scenarios 
and attack vectors that are commonly encountered in a typical network environment. Each 
test case is designed to evaluate a specific aspect of the security controls in place, such as 
the IDS, firewall, or packet sniffer, to ensure that they are functioning correctly and can detect 
and prevent security threats. Additionally, there are some chosen test cases that are specific 
to the project.
The first test case is used to ensure that the machine learning algorithm can correctly identify 
attacks with the use of a dataset. This was done to guarantee that the algorithm is reliable and 
efficient when analysing data. 
001090797
32 | P a g e
In addition to the first test case the second test case is used to determine if the algorithm can 
detect normal traffic and ensure that it can differentiate between an attack and normal traffic.
Furthermore, the third test case is important as an empty dataset can be a valid input for 
certain types of application. Furthermore, if the IDS is unable to handle an empty dataset 
properly, it may produce false positives or false negatives, thus leading to unnecessary alerts 
or missed security threats. 
For the fourth test the initial output failed however, the error that occurred was fixed. It is 
important to verify that the algorithm can analyse the data that the Packet Sniffer collects as 
the determines if the entire project is successful. This was accomplished by ensuring that the 
Packet sniffer can collect the same data as dataset used to train the machine learning 
algorithm. 
Test case number five is included as it is vital that the intrusion detection system can detect 
and log all events that occur. This includes anomalies, normal traffic, and an empty dataset, 
as well as provide an output for the user to investigate.
The sixth test was implemented to confirm that the honeypot is functional. This was tested by 
ensuring that honeypot can be deployed on a singular or multiple ports as well as log various 
attacks that may occur. This is important as it could provide the user with a deeper
understanding on the types of attacks used on the network and if there may be any 
vulnerabilities within the system.
Test case seven was implemented to verify if the firewall is active on the ports that were 
chosen by the user. This was achieved by running a simple Nmap scan on the chosen ports, 
if the Nmap results came back as “filtered”, this identifies that the firewall is active. 
The next test, test case eight, is used to validate if the port scanner is successful. The port 
scanner should provide the user with an output of all the open TCP and UDP ports on the 
network. This is vital as it correlates with the use of both the firewall and honeypot.
The ninth test is a preliminary test to ensure that the packet sniffer is functional, and that the 
data is logged and saved to a CSV file. This is essential as the detection system requires data 
from the saved files. 
For the final test, this is used to verify that all the graphical user interfaces are functional and 
provide the user with a user friendly and simplistic design. This was accomplished with the 
use of the Tkinter library in Python. 
4.4 Evaluation of XGBoost algorithm
From the above figure the XGBoost classifier model is loaded and used to predict the type of 
network traffic for each entry in the pre-processed data.
Table 2. XGBoost Performance Table
Class Precision Recall F-score Support
0 1.000000 1.000000 1.000000 551
1 1.000000 0.875000 0.933333 8
2 0.200000 0.500000 0.285714 2
3 1.000000 1.000000 1.000000 13
4 1.000000 0.666667 0.800000 3
5 1.000000 0.993590 0.996785 312
6 0.600000 0.600000 0.600000 5
001090797
33 | P a g e
7 1.000000 1.000000 1.000000 2
8 0.000000 0.000000 0.000000 2
9 1.000000 0.999888 0.999944 26800
10 0.950820 1.000000 0.974790 58
11 0.999342 0.999671 0.999507 24319
12 1.000000 1.000000 1.000000 1
13 1.000000 1.000000 1.000000 1
14 1.000000 1.000000 1.000000 66
15 0.988550 0.996154 0.992337 260
16 0.500000 0.666667 0.571429 3
17 1.000000 0.987406 0.993663 397
18 1.000000 0.999957 0.999979 70197
19 1.000000 1.000000 1.000000 245
20 1.000000 0.996078 0.998035 255
21 0.800000 0.800000 0.800000 5
The output table (Table***) displays the performance metrics (Precision, Recall, F-score, and 
Support) for each class (attack type or normal). Furthermore, each row represents, index from 
0 to 21 and each column represents a metric:
• Precision: This is the performance metric that quantifies the accuracy of the model’s 
positive prediction for each class. A high precision indicates that when a model predicts 
an instance to be in a particular class, it is more likely to be correct.
The calculation for Precision is as follows:
Precision = (True Positives)/ (True Positives + False Positives)
• Recall: This is a performance metric that quantifies the proportion of actuals positive 
instances that were correctly identified by the model for each class. A higher recall 
indicates that the model can identify more positive instances correctly.
The calculation for Recall is as follows: 
Recall = (True Positives)/ (True Positives + False Negatives)
• F-score (F1-score): This is a performance metric that balances the trade-off between 
precision and recall for each class. Furthermore, giving more importance to both false 
positives and false negatives. The higher the F-score, the better the performance of 
the model.
The calculation for F-score is as follows:
F-score = 2*(Precision * Recall)/ (Precision + Recall) 
• Support: This refers to the number of actual occurrences of each class. Furthermore, 
it gives an idea of the distribution of the classes in the test data and helps to provide a 
context on how balanced or unbalanced the dataset is. Additionally, a class with a 
higher support have a more significant impact on the model’s overall performance.
• Good performance:
Classes with high precision, recall, and F-score values (e.g., classes 0, 3, 9, 11, 18, 19, 
and 20) indicate that the model can accurately predict instances of these classes and has 
a low rate of misclassification.
001090797
34 | P a g e
• Moderate performance:
Classes with moderate precision, recall, and F-score values (e.g., classes 1, 4, 5, 10, 15, 
and 17) show that the model has some success in predicting instances of these classes, 
but there is still room for improvement.
• Poor performance:
Classes with low precision, recall, and F-score values (e.g., classes 2, 6, 8, and 16) 
indicate that the model struggles to predict instances of these classes accurately. There 
might be a higher chance of misclassification for these classes, either as false positives or 
false negatives.
From evaluating the performance of the model as well as the classes, the XGBoost algorithm 
performs well overall, however it does have difficulty predicting some classes accurately.
4.5 The Evaluation of Data tested
The evaluation of data tested for the intrusion detection and the XGBoost algorithm is an 
essential step in determining the effectiveness and accuracy of the IDS. This evaluation 
involves analysing the output generated by the XGBoost algorithm, which is used to classify 
network traffic as either normal or malicious, and comparing it to the actual behaviour of the 
network. The evaluation may include metrics such as the precision, recall, and accuracy of 
the algorithm, as well as the false positive and false negative rates.
The results of the evaluation can provide valuable insights into the performance of the IDS 
and help identify areas for improvement. For example, if the IDS generates a high number of 
false positives, it may be overly sensitive and need to be fine-tuned to reduce the number of 
false alerts. On the other hand, if the IDS generates a high number of false negatives, it may 
be missing potential security threats and need to be configured to detect a wider range of 
malicious activity.
In summary, the evaluation of data tested for the intrusion detection and the XGBoost 
algorithm is crucial for ensuring the accuracy and effectiveness of the IDS. By analysing the 
output generated by the algorithm and comparing it to the actual behaviour of the network, 
you can identify any discrepancies or areas for improvement and make informed decisions to 
improve the overall security and reliability of your system or network.
4.6 Critical Analysis of IDS
Throughout the production of the intrusion detection system, the implementation of the 
XGBoost algorithm and the additional security controls such as the honeypot, firewall, and 
port scanner appear to be a strong and effective approach for detecting and preventing 
potential security threats. Furthermore, certain choices were made throughout the production 
of the project for example, the methodology and the programming language used. The 
methodology refers multiple parts of the project, this includes, the functional and nonfunctional requirements, diagrams chosen to demonstrate and outline the lifecycle of the 
project as well as the decisions made during the project.
001090797
35 | P a g e
By implementing the functional and non-functional requirements before the creation of the 
project, this aided in producing a functional and useful application. Furthermore, by doing so, 
the application was able to meet the success criteria specified in the methodology. In addition 
to this the use of the use case diagram and the waterfall method were followed rather strictly, 
thus demonstrating that they were both effective and successful in their purpose.
The use of the XGBoost algorithm for classifying network traffic as either normal or malicious 
is a powerful tool that can significantly improve the accuracy and effectiveness of the IDS. 
This algorithm has been shown to perform well in a variety of use cases and can be tuned to 
meet specific requirements and security needs. Furthermore, the machine learning algorithm 
was chosen as the algorithm is simplistic, effective, and relatively fast. Additionally, the 
inclusion of a honeypot, firewall, and port scanner provides additional layers of defence
against potential threats and helps to ensure that your system or network is secure and 
reliable.
However, to fully evaluate the effectiveness of the IDS, it would be necessary to conduct 
further testing and analysis to determine the accuracy and reliability of the system. This may 
involve simulating real-world attack scenarios, testing the system against a variety of threat 
vectors, and analysing the results to identify any areas for improvement or fine-tuning.
Furthermore, to improve the IDS it is important to consider the experimenting with different 
algorithms or to tune hyperparameters to improve the overall performance of the model as 
well as to investigate class imbalance and apply techniques like oversampling, under 
sampling, or synthetic data generation to balance the dataset.
Furthermore, it is important to note that security is an ongoing process, and it is important to 
regularly review and update the security controls to ensure that they are effective against new 
and evolving threats. This may involve implementing new security technologies, updating 
existing controls, or conducting regular security audits to identify any potential vulnerabilities 
or weaknesses.
In conclusion, the implementation of an intrusion detection system with the XGBoost algorithm 
and additional security controls such as the honeypot, firewall, and port scanner are a strong 
and effective approach for securing network. However, to fully evaluate its effectiveness and 
ensure ongoing security, it is important to conduct regular testing and analysis and to stay up 
to date with the latest security technologies and best practices.
001090797
36 | P a g e
4. General Summary and Conclusions 
5.1 Summary of Project
This project has seen research into the field of network security, especially with regards to the 
implementation of intrusion detection systems and they ways in which the monitoring and 
analysing of data can be utilised to heighten the overall security of a network. The research 
and analysis that were conducted, provided vital information on the current level of network 
security as well as an insight on the prevention of data breaches. Furthermore, studies in 
which an intrusion detection system with the implementation of machine learning was used to 
enhance the overall security of a network, for an instance, the detection of different 
5.2 Limitations and Future Work
Despite the success of the intrusion detection system there are areas in which during the 
creation have arisen as possible objectives and additional functionalities that could be 
implemented to better the effectiveness and efficiency of the system. However due to time 
constraints and a lack of resources, these implementations not been employed yet. Moreover, 
given both future research and time, additional features can be implemented to address the 
limitations present in the current code and aid in developing the IDS further. 
A current limitation of the intrusion detection system would be the analyses of data in realtime. Currently the IDS can scan the hosts’ network and capturing live network traffic, the user 
then save the file after enough data is collected and then analyses it using the machine 
learning algorithm. The key problem here, is that the IDS will only be able to determine if an 
attack is happening on the network after enough data is collected rather than at the current 
moment. This can be accomplished by altering the IDS from signature-based to Hybrid 
detection system, which involves the implementation of an anomaly-based IDS (Cahyo, 
Kartika & Riasetiawan, 2020). Alhakami et al., (2019) notes that an anomaly detection IDS 
works by establishing a baseline of normal network behaviour and the identifying deviations 
from that baseline as potential intrusion. The advantage changing the IDS to become Hybridbased is that provides a more comprehensive detection capability by combining the strengths 
of both types of IDSs.
Another key improvement that can be implemented is use of multiple machine learning 
algorithms. This can be beneficial as it can lead to improved detection performance and 
robustness (Mishra & Yadav, 2020).
5.3 Personal Reflection 
Through working on this project, I thoroughly enjoyed the process of using the skills I have 
acquired through my studies at the University as well as to expand my current knowledge into 
a deeper understanding. Furthermore, the topic of network security, detections systems, 
machine learning and the applications of python and its libraries are topics that interest me. 
This was done deliberately as this would help me develop new skills from which it will benefit 
me in my future as well as help establish a firm footing in the field of computer science. 
001090797
37 | P a g e
I have a strong passion for Cyber Security and engage in an interest in Machine Learning, 
therefore, I believe that my project must encompass these aspects of computer science in 
some relevant ways. Moreover, the security of both personal and organisational networks
sparks interest within my future prospects as it promotes relevancy to the ever-expanding use 
of technology and the growth in network-based connections. Throughout conducting the 
research depicted in this project, I have gained extensive amount of knowledge on the use of 
intrusion detection and prevention systems with the incorporation of machine learning 
algorithms to improve network security. Additionally, whilst conducting research, I was 
introduced to knowledgeable and profound statistics about the number of people affected by 
poor network security, as well as the types of attacks that cooperations may be vulnerable to. 
With the latter stated, I was encouraged to implement these fields of computer science into 
my project and alleviate some of the common issues regarding security on networks. As stated 
previously, the topic at hand has allowed me to expand my knowledge for future job 
opportunities that are included in cyber security, therefore ensuring that I have a deeper 
understanding of networks has enabled me to grasp an understanding of what expectations 
are required of me in the future and create a foundation to which I can develop my knowledge 
and skills. 
Throughout the development of my project, I established strong organisational and time 
management skills due to the intense pressure and work deadlines set by both me and the 
module. This in turn required me to create a detailed plan from the beginning of the entirety of 
the production lifecycle of the application. In addition to this, a constant monitoring of the 
application was demonstrated, ensuring the project held to the success criteria and function 
requirements created by myself at the start. The conditions of the application () is an indication 
of the newfound knowledge that I have gained. Likewise, when developing the project, various 
diagrams (use case diagram and waterfall diagram) were used to show the progression and 
the evolution of the final product. These were extremely useful as they helped to create an 
image of what the application should feature as well as prove to be useful in future works. 
The most challenging part of the project was the creation of my application as I have never 
coded anything substantial in python prior to this project. This application taught me a great 
deal about the usefulness of the language as well as why it is one of the most popular 
languages in computer science. Also, through designing this project I have gained further 
knowledges on libraries such as Pandas, Tkinter, Scapy and Socket. Additionally, through 
researching and I have gained a deepener my understanding in the fields of network security 
and machine learning. This have helped my become more confident with Python and aid me 
in future projects.
Finally, if I were to undertake this project again with my current knowledge, I would take further 
steps into the information supplied in section ‘Future Works’. This includes advancing the 
current functionalities to cover a broader spectrum of cyber-attacks. Furthermore, I may have 
furthered my research in network analysis and machine learning to increase the accuracy of 
the current algorithm. 
001090797
38 | P a g e
5. References
Alhakami, W. et al., 2019. Network Anomaly Intrusion Detection Using a Nonparametric 
Bayesian Approach and Feature Selection. IEEE Access, Volume 7, pp. 52181-52190.
Amal, M. & Venkadesh, P., 2022. Review of cyber attack detection: Honeypot system. 
Webology, 19(1), pp. 5497-5514.
Amarudin , Ferdiana, R. & Widyawan, 2020. A Systematic Literature Review of Intrusion 
Detection System for Network Security: Research Trends, Datasets and Methods. In: 2020 
4th International Conference on Informatics and Computational Sciences (ICICoS). 
Semarang: IEEE, pp. 1-6.
Amos, D., 2020. Python gui programming with tkinter. Tersedia: https://realpython. 
com/python-gui-tkinter.
Aslan, Ö. et al., 2023. A Comprehensive Review of Cyber Security Vulnerabilities, Threats, 
Attacks, and Solutions. Electronics, 12(6).
Cahyo, A. N., Kartika Sari, A. & Riasetiawan, M., 2020. Comparison of Hybrid Intrusion 
Detection System. In: 2020 12th International Conference on Information Technology and 
Electrical Engineering (ICITEE). Yogyakarta: IEEE, pp. 92-97.
Chang, V. et al., 2022. Future Internet. A Survey on Intrusion Detection Systems for Fog and 
Cloud Computing, 14(3).
Devi, B. T., Shitharth, S. & Jabbar, M. A., 2020. An Appraisal over Intrusion Detection Systems 
in Cloud Computing Security Attacks. In: 2020 2nd International Conference on Innovative 
Mechanisms for Industry Applications (ICIMIA). Bangalore: IEEE, pp. 722-727.
Eltanbouly, S. et al., 2020. Machine Learning Techniques for Network Anomaly Detection: A 
Survey. In: 2020 IEEE International Conference on Informatics, IoT, and Enabling 
Technologies (ICIoT). Qatar: IEEE, pp. 156-162.
Falcão, F. et al., 2019. Quantitative comparison of unsupervised anomaly detection algorithms 
for intrusion detection. Cyprus, Association for Computing Machiner.
Group, T. 2022 Thales Data Threat Report - Global Edition, Data Breach 2022 - Report. 
Available at: https://cpl.thalesgroup.com/resources/encryption/2022/data-threat-report 
(Accessed: January 28, 2023).
Goodman , H. B. & Rowland, P., 2021. Deficiencies of Compliancy for Data and Storage. In: . 
K. R. Choo, T. Morris, G. L. Peterson & E. Imsand, eds. National Cyber Summit (NCS) 
Research Track 2020. s.l.:Springer International Publishing, pp. 170-192.
Gurung, S., Ghose, M. K. & Subedi, A., 2019. Deep Learning Approach on Network Intrusion 
Detection System using NSL-KDD Dataset. International Journal of Computer Network and 
Information Security, 11(3), pp. 8-14.
Hajj, S. et al., 2021. Anomaly-based intrusion detection systems: The requirements, methods, 
measurements, and datasets. Transactions on Emerging Telecommunications Technologies, 
32(4), p. 4240.
Kilincer, I. F., Ertam, F. & Sengur, A., 2022. A comprehensive intrusion detection framework 
using boosting algorithms. Computers and Electrical Engineering, Volume 100, p. 107869.
001090797
39 | P a g e
Kumar, V. & Sangwan, O. P., 2012. Signature Based Intrusion Detection System Using 
SNORT. International Journal of Computer Applications & Information Technology, 1(3), pp. 
35-41.
Liang, J. & Kim, Y., 2022. Evolution of firewalls: Toward securer network using next generation 
firewall. In: 2022 IEEE 12th Annual Computing and Communication Workshop and 
Conference (CCWC). Las Vegas: IEEE, pp. 752-759.
Lundin, E. & Jonsson, E., 2002. Survey of intrusion detection research, s.l.: Chalmers 
University of Technology.
Mallaboyev, N., Sharifjanovna, Q. M., Muxammadjon, Q. & Shukurullo, C., 2022. 
INFORMATION SECURITY ISSUES. In: Conference Zone. Berlin : s.n., pp. 241--245.
Mishra, A. & Yadav, P., 2020. Anomaly-based IDS to Detect Attack Using Various Artificial 
Intelligence & Machine Learning Algorithms: A Review. In: 2nd International Conference on 
Data, Engineering and Applications (IDEA). Bhopal: IEEE, pp. 1-7.
Nidhra, S. & Dondeti, J., 2012. Black box and white box testing techniques-a literature review. 
International Journal of Embedded Systems and Applications (IJESA), 2(2), pp. 29-50.
Othman, S. M., Alsohybe, N., Ba-Alwi, F. M. & Zahary, A. T., 2018. Survey on intrusion 
detection system types. International Journal of Cyber-Security and Digital Forensics, 7(4), 
pp. 444-463.
Overill, R. E., 2004. Reacting to cyber-intrusions: the technical, legal and ethical dilemmas. 
Journal of Financial Crime, 11(2), pp. 163-167.
Parker, D. M., Pine, S. G. & Ernst, Z. W., 2018. Privacy and informed consent for research in 
the age of big data. Penn St. L. Rev., Volume 123, p. 703.
Patel , A., Taghavi, M., Bakhtiyari, K. & Celestino, J., 2013. An intrusion detection and 
prevention system in cloud computing: A systematic review. Journal of Network and Computer 
Applications, 36(1), pp. 25-41.
Radivilova, T. et al., 2020. The Complex Method of Intrusion Detection Based on Anomaly 
Detection and Misuse Detection. In: 2020 IEEE 11th International Conference on Dependable 
Systems, Services and Technologies (DESSERT). Ukraine: IEEE, pp. 133-137.
Singh, A., 2019. Socket Programming With Python. s.l.:Lulu Press, Inc.
Soniya, S. & Vigila, M. C., 2016. Intrusion detection system: Classification and techniques. In: 
2016 International Conference on Circuit, Power and Computing Technologies (ICCPCT). 
Nagercoil: IEEE, pp. 1-7.
Srinivas, J., Das, A. K. & Kumar, N., 2019. Government regulations in cyber security: 
Framework, standards and recommendations. Future Generation Computer Systems, Volume 
92, pp. 178-188.
Tahsien, . S. M., Karimipour, H. & Spachos, P., 2020. Machine learning based solutions for 
security of Internet of Things (IoT): A survey. Journal of Network and Computer Applications, 
Volume 161, p. 102630.
The Evolution of Endpoint Security (no date) News & Events. Available at:
https://disa.mil/newsandevents/2018/evolution-endpoint-security (Accessed: March 15,2023). 
001090797
40 | P a g e
Tufan, E., Tezcan, C. & Acartürk, C., 2021. Anomaly-Based Intrusion Detection by Machine 
Learning: A Case Study on Probing Attacks to an Institutional Network. IEEE Access, Volume 
9, pp. 50078-50092.
Vanschoren, J. (no date) KDDcup99 Dataset, OpenML. Available at:
https://www.openml.org/search?type=data&sort=runs&id=1113&status=active(Accessed: 
April 23, 2023). 
Wahal , M., Choudhury , T. & Arora, M., 2018. Intrusion Detection System in Python. In: 2018 
8th International Conference on Cloud Computing, Data Science & Engineering (Confluence). 
Noida: IEEE, pp. 348-353
