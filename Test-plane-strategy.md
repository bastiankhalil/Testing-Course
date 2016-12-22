****Prepared By** :** The Test Lead
# My Web Server



# Chapter 1

# **1- Introduction**
Testing is a very important stage of any software production. Between our hands a web server. The following pages demonstrate the Test strategy, test-plan, test-cases and the reports of our testing.

# **2- Testing goals and objectives**

This document describes the plan and the strategy for testing the main functionality of &quot;My Web Server&quot; application which has been provided by application stakeholders. We will make sure to detect if the webserver:

- Responsive under high load.
- Follow minimum requirements for HTTP 1.1
- Works Windows 10.
- Source code released under GPL-2.0.
- Access log viewable from a text editor.

By doing this we should uncover if there is any errors in our server software and build confidence.


----------


# **3- TEST STRATEGY**
####**3.1) Iterations ( Test Schedule ):**
Since we have 40 Hours and one week then is is logical to have 1 Agile iteration. Tow weeks eveyday 4 hours.

###**3.2) Testing Level:**

Level 1:

|   Key|  Explanation|
|---|---|
| WHY  | To make sure the server support HTTP |
|  WHAT     |   Manual Testing |
|  WHERE  |  Local Development Environment |
|   HOW    |  Using Java, Eclipse and Junit test framework|

Level 2:

|   Key|  Explanation|
|---|---|
| **WHY**        | To make sure the server responsive under very high load |
| **WHAT**      |  Stress testing  |
|  **WHERE**  | Local Development Environment  |
|  **HOW**       |  Using Apache Jmeter testing application. |





Level 3:

|   Key|  Explanation|
|---|---|
| WHY  | To make sure the server integrated with a socket client |
|  WHAT     |   integration test |
|  WHERE  |  Local Development Environment |
|   HOW    |  Using Java, Eclipse and Junit test framework|

Level 4:

|   Key|  Explanation|
|---|---|
| WHY  | To make sure the server runs some basic functions |
|  WHAT     |   Unit test |
|  WHERE  |  Local Development Environment |
|   HOW    |  Using Java, Eclipse and Junit test framework|


###**3.3) Risk &amp; Mitigation**

Risk is future&#39;s uncertain event with a probability of occurrence and a potential for loss. Here is some the risks and what actions to be takes if they happens.

|  RISK  | Mitigation  |
|---|---|
|  I may lack the required skills to test certain part of the application that is required | Search the internet for an answer or propose a question on slack testing group  |
|  The project schedule is too tight; it&#39;s hard to complete this project on time. |  Set Test Priority for each of the test activity |
|  Wrong time estimate |  Establish the scope before beginning work, pay a lot of attention to project planning and constantly track and measure the progress.  |

###**3.4) Roles and Responsibilities:**

**Roles** : It&#39;s is me as a test lead and a tester.
**Responsibilities** :

- Make sure every test case / use case has been done ideally.
- Make sure that the test cover all the requirements of the stakeholders.
- Make sure the test cases results are reported.

###**3.5) Environment Requirements:**

The tester must have:

- Windows 10 machine updated to the latest patch.
-   [Apache JMeter™ (  apache-jmeter-3.1.tgz )](http://jmeter.apache.org/) installed ( The same version ).
- [Jmeter plugin installer](https://jmeter-plugins.org/install/Install/)  installed and at least HTTP plugin and its dependencies installed.
- Watched the video on JMeter intro.

###**3.6) Means and tools:**

 - Windows machine.
 - Internet connection.
 - Eclipse.
 - command line tool.

###**3.7) Requirements traceability matrix:**

Ideally, the software must completely satisfy the set of requirements. We can illustrate that using the **Requirements tractability matrix table** HERE


----------


# **4- TEST PLAN**

###**4.1) Functional Requirements: ( What should be tested? )**

| Id  |Actor   | Requirement |
|---|---|---|
|REQ-01  | server administrator  | I want to be sure that the server is responsive under high load. |
|REQ-02|  server administrator | I want to be sure that the server follow minimum requirements for HTTP 1.1  |
|REQ-03| server administrator  |  I want to be sure that the server works on Linux, Mac, Windows\*.  |
|REQ-04|  server administrator |  I want to be sure that the server released under GPL-2.0. |
|REQ-05|server administrator| I want to be sure that the server access log viewable from a text editor.|


###**4.2) Use Cases:** 


####**Use Case 1 (Start Server)**:
**Primary Actor:**  Administrator.
**Postcondition:**

 - A web server has been started.
 - A note in the access log was written, that the server was started.

**Main scenario:**

 1. Starts when an administrator wants to start the server.
 2. System asks for socket port number and shared resource container.
 3. The administrator provides a socket port number and a shared resource container.
 4. System starts a web server on the given port and presents that the server was started and writes a note in the access log.

**Alternate Scenarios:**

 - 4a. The web server could not be started due to socket was taken:
	 -  System presents an error message: “Socket XX was taken” (XX is the socket number, Example “80”).
	 - Exit Use Case
 - 4b. The web server could not be started due restriction on the shared resource container:
	 - System presents an error message: “No access to folder XX” (XX is the shared resource container provided, Example “\var\www”).
	 - Exit Use Case.
 - 4c. The access log could not be written to:
	 - System presents an error message. “Cannot write to server log file log.txt”
	 - Exit Use Case.

####**Use Case 2 (Stop Server):**

**Primary Actor:**  Administrator.
**Precondition:**

 - A web server has been started.

**Postcondition:**

 - A note in the access log was written, that the server was stopped.

**Main scenario:**

 - 1 -Starts when a user wants to stop the server.
 - 2- System stops the web server and presents that the web Server has been stopped. 

####**Use Case 3 (Request shared resource):**

**Primary Actor :** Browser.

**Precondition :** 

 - A web server has been started.

**Post condition:** 

 - A note in the access log was written, that access happened with request information and the result of the request.

**Main scenario:** 

 - 1 -  Starts when a Browser wants to access a shared resource.
 - 2 - System delivers the shared resource to the browser and a success message is written to the access log. 

**Alternate Scenarios:** 

 - 2a: The shared resource cannot be found
	 - System presents that the resource cannot be found
	 - Exit Use Case
 - 2b: The shared resource is outside the shared resource container.
	 - System presents that the resource is forbidden
	 - Exit Use Case
 - The resource request is invalid or malformed.
	 - System presents that the request cannot be handled.
	 - Exit Use Case.
 - 2d: The server encounters an error when trying to process the request.
	 - System presents that it has an internal error.
	 - Exit Use Case.

**Technical note:** 

 - Browser and System communicates using HTTP 1.1.
 - Error messages are part of HTTP 1.1 protocol.
	 - 200 OK
	 - 400 Bad request
	 - 403 Forbidden
	 - 404 Not Found


###**4.3) Non-Functional Requirements:** 
As we know the **Non-Functional Requirements** is the system's overall properties commonly mark the difference between whether the development project has succeeded or failed.

 - **NF-REQ01**:  *The system should be*  redistributable on a wide range of Internet Of Things (IOT).
 - **NF-REQ02** *The system should be* easy to deploy web-server that can be deployed on many different devices.
 - **NF-REQ03** *The system should be* easy integration and adaptation.
 - **NF-REQ04** *The system should be* easy to do the configuration.
 - **NF-REQ05** *The system should be* very secure.
 - **NF-REQ06** *The system should be* easy to access.

###**4.4) Prioritization:** 
The maximum  propriety for me as a tester to meet the core requirements of the stakeholders gave us which is:

 - The functional requirements ( REQ-01 to REQ-50)
 - The main three use cases 1 to 3.
 
###**4.5) How should we test:** 
#### **Technologies  we will use**:
 - Exploratory Testing.
 - Stress Testing. 
 - Integration Testing.
 
###**4.6) Test Report Form:** 
The testing results will be presented as a single Markdown file ( this one ). It will contains a table of each requirement ans its test cases in on of the following status:
<ol>
<li> <b>Succeed:</b> a mark conform that this test case has passed </li>
<li> <b>Fail:</b> A mark confirm that this test case is failed  <b>and how to reproduce the fail status</b></li>
</ol>

**Traceability to requirements table will be provided that illustrate the whole result of the tests.**
 

------------------------------------------------------------------------------------------------------------------

#  Chapter 2

## **1- Preface**
As we have written our test strategy and test plane and then did what we have planed its time to know the result of the test. The following pages is a result reports of our test cases.

## **2- Purpose**
Our main purpose of these papers is to summarize the tests results and efforts so they can presented to the steakholders.

## **3- Requirements based test results**

| ID | case | Succeed Rate | Fail Rate | Notes |
| ------------- |:-------------| :-----:| :-----: | :-----: |
| REQ-01 | 50 HTTP request with 50 sec delay = 500 requests  |  100%  | 0 |  | 
|      | 100 HTTP request with 100 sec delay = 1000 requests  |  100% | 0 |  |
|      | 1000 HTTP request with 100 sec delay = 11000 requests |  100%  | 0 | [Screenshot Here ](http://vianx.com/testing/01.png) |
| REQ-02 | sending request from type =  GET|  100%  | 0 |  | 
|  | sending request and response from type =  GET|  100%  | 0 |  | 
|  | sending request and response =  HEAD|  100%  | 0 |  | 
|  | sending request and response =  POST|  100%  | 0 |  | 
|  | sending request and response =  PUT|  100%  | 0 |  | 
|  | sending request and response =  PATCH|  100%  | 0 |  |
| REQ-03 | the server works properly on windows |  100%  | 0 |  | 
|  | the server works properly on windows with customize ports |  100%  | 0 |  |
| REQ-04 |server released under GPL-2.0. |  0  | 100% |  | 
| REQ-04 |server  access log viewable from a text editor. |  0  | 100% |  | 
| REQ-04 |server access log viewable from a text editor |  0  | 100% | the intenstion is a file and not the console log  | 
| **UC1** | Main scenario |  0  | 0|
| |Alternate Scenario A |  100%  | 0 |
| |Alternate Scenario B |  100%  | 0 |
| |Alternate Scenario C |  0  | 100% | there is no log.txt |
| **UC2** | Main scenario |  100%  | 0| consider the log as the console log  window|
| **UC3** | Main scenario |  100%  | 0| consider the log as the console log  window|
| |Alternate Scenario A **Status Code:404 Not Found** |  100%  | 0 | [Screenshot Here ](http://vianx.com/testing/40000.png)|
| |Alternate Scenario B  **Status Code:403 Forbidden**|  100%  | 0 |
| |Alternate Scenario C **Status Code:400 Bad request**|  100%  | 0 |
| |Alternate Scenario D **Status Code:500 Internal Server Error**|  100%  | 0 |
| **Integration Testing** | Integration HTTP Server Test  |  100%  | 0 |
|  | Integration Stress Test|  100%  | 0 |
|  | Integration Socket Client Test|  0  | 100% |
| **Response Test** | Response Error Responses  |  100%  | 0 |
|  | Response Content Type Test |  100%  | 0 |
|  | Response HTML file Response Test |  100%  | 0 |
| **View Test** | Test No Argument  |  100%  | 0 |
|  | Test Port is set |  100%  | 0 |
| | Test Port is taken |  0  | 100% |


## **4- Test Results Summery**

| Test | Succeed Rate | Fail rate |
| ------------- |:-------------:| :-----:|
|Acceptance to requirements test |70%|30%|
|Use cases Tests |60%|40%|

