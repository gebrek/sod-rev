
# Table of Contents

1.  [Introduction](#org77006bd)
    1.  [Purpose](#orgf35e128)
    2.  [Assumptions](#org06bd283)
    3.  [Terminology](#org40e0ad6)
2.  [Business Domain](#org8cc55ab)
    1.  [Usage Scenarios](#orgc7a30b6)
        1.  [Student Case](#org8fa2d1d)
        2.  [Cafeteria Case](#org8d209e5)
    2.  [Participants](#org666a7ba)
        1.  [Stakeholders](#orged6d7cc)
        2.  [Users](#orgd986f9d)
    3.  [Model](#org394bc90)
    4.  [Conceptual Services](#org09b2b18)
        -   [Preorder Service](#org4c1f613):hybrid:
        -   [Prediction Service](#org98896ef):hybrid:
        -   [Menu Changing Service](#org29965e1):task:
        1.  [View Service](#org6971e07):entity:
3.  [Functional Requirements](#org34c4c84)
    -   [*Requirements*](#org347507a)
        -   [\* FR-01 : *Placing Orders*](#orgc02f4c8)
        -   [FR-02 : *Schedule Pickup*](#orgca0c859)
        -   [FR-03 : *Electronic Payment*](#orgb66f2b1)
        -   [\* FR-04 : *Record Transactions*](#org36f5040)
        -   [FR-05 : *Send Transactions Records*](#orgc5ea1bf)
        -   [FR-06 : *Send Cafeteria Orders*](#org0f4e4de)
        -   [FR-07 : *Authorization*](#org0c331a6)
        -   [\* FR-08 : *Trend Analysis*](#orgc817c2f)
4.  [Quality Requirements](#org152e48c)
    1.  [QR-01 : *Security*](#org7d78a20)
    2.  [QR-02 : *Availability*](#org45c3b4c)
    3.  [QR-03 : *Usability*](#org3216b1d)
    4.  [QR-04 : *Reliability*](#orgc6788d9)
5.  [Business Services](#org2d4c15e)
    1.  [BS-01 : *Transaction Recording*](#org921e0d1)
        1.  [Involved Participants](#orga8d6e96)
        2.  [Detailed Operational Description](#orge755f7c)
        3.  [Service Behavior](#org42dec4c)
        4.  [Service Decomposition](#org0ed1822)
    2.  [BS-02 : *Statistical Analysis*](#orgb51bb9c)
        1.  [Involved Participants](#org8888b10)
        2.  [Detailed Operational Description](#org8dbf822)
        3.  [Service Behavior](#orgf8a56c3)
        4.  [Service Candidates Decomposition](#orgf83e7e2)
    3.  [BS-03 : *Preordering*](#orgb279d84)
        1.  [Involved Participants](#org0224775)
        2.  [Detailed Operational Description](#org758f830)
        3.  [Service Behavior](#orgfbd820f)
        4.  [Service Decomposition](#org9881a1b)
6.  [Design Space](#org1f419d5)
    -   [AK-SPAM](#orge16e09a)
        -   [Concern](#org69bc15e)
        -   [Criteria](#orgcd1cc9a)
        -   [Options](#org76c4ede)
        -   [QOC Diagram](#org4b1b738)
7.  [Sustainability Strategies](#org1e73d65)



<a id="org77006bd"></a>

# TODO Introduction


<a id="orgf35e128"></a>

## Purpose

This document presents a design aimed at reducing waste, caused by
a university cafeteria over-producing food, by using a pre-ordering
service along with historical analysis to provide accurate
short-term demand estimates as well as insight into overall trends.


<a id="org06bd283"></a>

## TODO Assumptions


<a id="org40e0ad6"></a>

## TODO Terminology

![img](res/decomp_example.png)

![img](res/qoc_example.png)


<a id="org8cc55ab"></a>

# DONE Business Domain


<a id="orgc7a30b6"></a>

## DONE Usage Scenarios


<a id="org8fa2d1d"></a>

### Student Case

Frank and Giorgia are sitting in class taking notes on their
laptops. They want to eat at the Cafeteria before their next
lecture. The University Cafeteria has a wide variety of food
available, and Frank is hungry so he looks up the Cafeteria's menu
and decides to get fish and chips with a side of salad. Giorgia
does the same, but also places an order and schedules to pick it
up in thirty minutes.

Frank and Giorgia leave class and go the Cafeteria. When they
arrive Frank looks around for his desired meal, but does not see
it. Another batch of fish and chips is being made and he'll have
to wait or choose something else. 

Giorgia instead goes to a kiosk labeled "Pick-up" and tells the
clerk her name and order number. The clerk fetches her meal, and
she goes to pay the cashier.


<a id="org8d209e5"></a>

### Cafeteria Case

At the beginning of a new day cooks in the Cafeteria begin
preparing that day's meals. For the most part they stick to a
routine menu with items appearing on and disappearing from the
menu at regular intervals for various reasons. Whether because of
shortage or to keep the menu fresh. This is the core menu.

They also prepare some meals that have already been ordered for
the morning. Which are placed in temporary storage, organized for
quick retrieval and preserved to keep the hot and cold items
fresh. Students come and go picking up their orders, or taking
time choosing a meal. Some 

The kitchen notices that a particular item is selling less than
usual and by the end of the day there looks to be an excess amount
of waste. The kitchen signals to the computer system that it
should promote this item in some way. Either through a banner in
the app, placing the item nearer to the top of the menu, putting
on a token sale of the item, or whatever other promotional
method.

At the end of the month the kitchen notices that some items were
unpopular based off of the sales statistics. The kitchen then
decides that they will take those items off the menu, or make less
for the next month.


<a id="org666a7ba"></a>

## DONE Participants


<a id="orged6d7cc"></a>

### Stakeholders

1.  **University**

    The university will provide a preordering service for students
    and a notification service for the Cafeteria, informing it of
    students' orders.
    
    Additionally the University will be recording transactions made
    through the preorder service (and those made without it) so that
    the data may later be analyzed.

2.  **Digital Payment Processor**

    A Digital Payment Processing company provides exactly such a
    service, processing pre-order payments made through an online
    service.


<a id="orgd986f9d"></a>

### Users

1.  **Cafeteria**

    The Cafeteria serves food to Students, receiving orders directly
    from a student or indirectly via the University's
    preorder/notification service. The Cafeteria will also report
    sales and unsold product. The Cafeteria produces the supply.

2.  DONE **Students**

    A Student of the University is a customer of the
    Cafeteria. Students are the entities which generate demand.


<a id="org394bc90"></a>

## DONE Model

![img](res/business_domain.png)


<a id="org09b2b18"></a>

## TODO Conceptual Services

This section contains a list of every service that could be related
to the operation of the proposed system. In it are both software
and non-software services, we will describe the details of some of
the former and assume the latter will be provided by other
entities.


<a id="org4c1f613"></a>

### Preorder Service     :hybrid:

The service by which Students can communicate their demand ahead
of time.

-   **Authorization Service**     :utility:

    Provided by the University for the Students, Cafeteria, and
    University Administrators. Serves as a secure gateway for
    accessing software components of the system.
    
    -   Registration Service     :utility:
    
    -   Login Service     :utility:

-   **Online Ordering Service**     :hybrid:

    Provided by the University for the Students. An internet gateway
    Students use to interact with the system.
    
    -   (Menu) Viewing Service     :entity:
    
    -   Shopping Cart Service     :entity:
    
    -   Scheduling Service     :task:

-   **Notification Service**     :task:

    Provided by the University to the Cafeteria. Informs the
    Cafeteria of what orders have been placed, the contents of the
    order and the desired pickup time.

-   **Digital Payment Service**     :utility:

    Provided by the Digital Bank stakeholder, if the Student wishes
    to pay at the time of preordering, they are transferred to the
    Digital Bank's service in order to complete the payment.

-   **Food Service**     :task:

    Non-software service provided the Cafeteria, performing manual
    labor required to complete orders.
    
    -   Food Preparation Service     :task:
    
        Fulfillment of Student orders.
    
    -   Order Validation Service     :task:
    
        Matching of a Student to their order at pickup.
    
    -   Food Fetching Service     :task:
    
        Retrieval of a Student's order at pickup.


<a id="org98896ef"></a>

### Prediction Service     :hybrid:

The service by which a prediction of demand in the short and long
term is made.

-   **Analysis Service**     :entity:

    Owned by the University. Analyzes collected data in order to
    develop a model for future demand.

-   **Record Service**     :task:

    Owned by the University. Records orders made through the preorder
    service or collects data regarding the other sales made at the
    Cafeteria.
    
    -   Reporting Service     :utility:
    
        Provided for the Cafeteria by the University. The Cafeteria
        reports sales made, preorders fulfilled, and excess production.

-   **Data Storage Service**     :task:

    The data the University collects on orders needs to be stored
    somewhere, whether this is done on an owned asset or if though a
    service provided by another stakeholder.

-   **(Data) Viewing Service**     :entity:

    The data which has been stored must be accessible for the
    University to perform analysis.


<a id="org29965e1"></a>

### Menu Changing Service     :task:

The Cafeteria has to be able to change the menu from week to week,
or over whatever time period the menu changes.


<a id="org6971e07"></a>

### View Service     :entity:


<a id="org34c4c84"></a>

# DONE Functional Requirements

In this section we list some of the functional requirements that our
services, as they are described, must fulfill. They have been
derived from the services outlined in the [Conceptual Services](#org09b2b18)
section. The format is:

-   **ID : *Name***
    
    Short Description

For our purposes we will select functional requirements most
relevant to the problem of accurately predicting demand. To this end
we will be concerned with FR-01 (*Placing Orders*), FR-04 (*Record
Transactions*), and FR-08 (*Trend Analysis*). These three functions
form a skeleton of the proposed service: when a Student places an
order, that data is collected by the University and saved for future
analysis. This means we will neglecting the Digital Bank
stakeholder, and perhaps only touching the actions of the
Cafeteria. The other functionalities listed are necessary but
peripheral to the core intent of this proposal.


<a id="org347507a"></a>

## *Requirements*


<a id="orgc02f4c8"></a>

### \* <a id="org713cf09">FR-01</a> : *Placing Orders*

A Student must be able to place an order without being physically
present at the Cafeteria


<a id="orgca0c859"></a>

### <a id="org52721aa">FR-02</a> : *Schedule Pickup*

As an order is placed, the Student should also be able to specify
a time they wish to obtain their order.


<a id="orgb66f2b1"></a>

### <a id="org12a3f8a">FR-03</a> : *Electronic Payment*

A Student should be able to optionally pay at the time of placing
their order.


<a id="org36f5040"></a>

### \* <a id="org5151181">FR-04</a> : *Record Transactions*

Each transaction made must be recorded.


<a id="orgc5ea1bf"></a>

### <a id="org5d490b3">FR-05</a> : *Send Transactions Records*

If a transaction is not made through the preorder system, the
Cafeteria must still report it to the University.


<a id="org0f4e4de"></a>

### <a id="orga53d472">FR-06</a> : *Send Cafeteria Orders*

There must be a system in place so that the Cafeteria receives
preorders as soon as possible.


<a id="org0c331a6"></a>

### <a id="orge2d54ec">FR-07</a> : *Authorization*

The system must be properly secured so that users of the system
may register, log in, and perform whatever actions that particular
user is permitted and no others.


<a id="orgc817c2f"></a>

### \* <a id="org21bc8f9">FR-08</a> : *Trend Analysis*

The system must have some way of extrapolating demand based on the
number of preorders, correlated with historical data.

---

All this and more&#x2026;


<a id="org152e48c"></a>

# TODO Quality Requirements

This section will discuss the most important qualities in
considering the problem of more accurately predicting and meeting
demand. For clarity we will use standard<sup><a id="fnr.1" class="footref" href="#fn.1">1</a></sup> definitions.


<a id="org7d78a20"></a>

## DONE <a id="org7de938c">QR-01</a> : *Security*

-   **Definition:** degree to which a product or system protects
    information and data so that persons or other
    products or systems have the degree of data access
    appropriate to their types and levels of
    authorization

We choose security because adoption of the system is predicated on
security. If the system is not secure and leaks important
information, or is otherwise compromised, trust in the system will
diminish to nothing. Any security faults regarding the online
payment process would be especially deleterious.


<a id="org45c3b4c"></a>

## TODO <a id="org0b4f6c3">QR-02</a> : *Availability*

-   **Definition:** degree to which a system, product or component is
    operational and accessible when required for use

The system must be reliably available to users on campus and off,
with as little down-time as possible. The end users rely on the
preorder service to order food ahead of time, and the University
relies on it to develop a model for demand


<a id="org3216b1d"></a>

## TODO <a id="orgc948a12">QR-03</a> : *Usability*

-   Note taken on <span class="timestamp-wrapper"><span class="timestamp">[2018-10-11 Thu 11:40] </span></span>   
    Update motivation
-   **Definition:** degree to which a product or system can be used by
    specified users to achieve specified goals with
    effectiveness, efficiency and satisfaction in a
    specified context of use

The students will want to be able to use the services quickly and
easily, because they only need to browse through the menu and place
an order, regardless of the device. If the service is too complex
to use they will not make pre-ordering a habit which contradicts
our goal of 


<a id="orgc6788d9"></a>

## TODO <a id="orgc9bb5dd">QR-04</a> : *Reliability*

-   **Definition:** degree to which a system, product or component
    performs specified functions under specified
    conditions for a specified period of time


<a id="org2d4c15e"></a>

# Business Services


<a id="org921e0d1"></a>

## <a id="org35e29d3">BS-01</a> : *Transaction Recording*


<a id="orga8d6e96"></a>

### TODO Involved Participants


<a id="orge755f7c"></a>

### TODO Detailed Operational Description


<a id="org42dec4c"></a>

### DONE Service Behavior

In this first activity diagram we will be more explicit about each
service involved, but we will abstract some (Authentication and
Response) away to simplify the other activity diagrams.

![img](res/bs_01_act.png)


<a id="org0ed1822"></a>

### DONE Service Decomposition

![img](res/bs_01_dcmp.png)


<a id="orgb51bb9c"></a>

## <a id="orgd44d32a">BS-02</a> : *Statistical Analysis*


<a id="org8888b10"></a>

### TODO Involved Participants


<a id="org8dbf822"></a>

### TODO Detailed Operational Description


<a id="orgf8a56c3"></a>

### DONE Service Behavior

![img](res/bs_02_act.png)


<a id="orgf83e7e2"></a>

### DONE Service Candidates Decomposition

![img](res/bs_02_dcmp.png)


<a id="orgb279d84"></a>

## <a id="orgbc14d95">BS-03</a> : *Preordering*


<a id="org0224775"></a>

### TODO Involved Participants


<a id="org758f830"></a>

### TODO Detailed Operational Description


<a id="orgfbd820f"></a>

### DONE Service Behavior

![img](res/bs_03_act.png)


<a id="org9881a1b"></a>

### DONE Service Decomposition

![img](res/bs_03_dcmp.png)


<a id="org1f419d5"></a>

# Design Space


<a id="orge16e09a"></a>

## AK-SPAM


<a id="org69bc15e"></a>

### Concern

-   **Con#1:** How can the user be encouraged to use the pre-ordering
    system? Are there any barriers or concerns that the
    customer or business would have that would make them
    not want to use it, undercutting the primary goal of
    reducing waste via this system?


<a id="orgcd1cc9a"></a>

### Criteria

-   **Cr#1:** Security
-   **Cr#2:** Availability
-   **Cr#3:** Usability


<a id="org76c4ede"></a>

### Options

-   Trusted Third Party Payment

    -   **ID:** Con#1-Opt#1
    -   **Description:** Pre-order payment should be done through a
        trusted and known third party with experience so
        the process is secure.
    -   **Status:** Decided
    -   **Relationship(s):** none
    -   **Evaluation:** &#x2014;
        -   Cr#1 &#x2014; This option is secure as long as the
            third party maintains integrity. While we have a little less
            control over the security of the system, a third-party
            payment processing company's business is predicated on
            security, so we assess this positively.
        -   Cr#2 &#x2014; This option's availability depends again on the
            third party, it is partially out of our control, depending on
            the service model of the third party.
        -   Cr#3 &#x2014; This option should have positive usability,
            especially if it is through an already common service that
            Students already use.
    -   **Rationale:** Given that the third-party processing company is
        of repute, this option should have the best
        security, availability, and usability. The same
        functionality is achieved as implementing it
        in-house but with a slight recurring cost.

-   Payment on Pickup

    -   **ID:** Con#1-Opt#2
    -   **Description:** There is no online payment system, the customer
        pays for items upon receipt.
    -   **Status:** Rejected
    -   **Relationship(s):** none
    -   **Evaluation:** &#x2014;
        -   Cr#1 &#x2014; This option is as secure as the Cafeteria itself. No
            additional attack vectors are added to the existing
            infrastructure.
        -   Cr#2 &#x2014; The rest of the system may still have high
            availability, but payment is only available when at the
            Cafeteria, so this option has a negative effect on
            availability.
        -   Cr#3 &#x2014; This option does nothing to improve usability,
            it does not enable Students to complete payment more than
            without the system so we assess this as negative in the
            usability dimension.
    -   **Rationale:** 

-   In-house Payment System

    -   **ID:** Con#1-Opt#3
    -   **Description:** 
    
    -   **Status:** 
    
    -   **Relationship(s):** 
    
    -   **Evaluation:** 
    
    -   **Rationale:** 


<a id="org4b1b738"></a>

### QOC Diagram

![img](res/qoc_01.png)


<a id="org1e73d65"></a>

# Sustainability Strategies


# Footnotes

<sup><a id="fn.1" href="#fnr.1">1</a></sup> ISO/IEC 25010:2011
