---
title: "Example"
date: 2018-08-21T00:36:38-03:00
---

Due to its similarity with the JSON’s definition, we believe developers are likely to have little trouble either to understand or to use Claret, particularly due to the fact that the intended use of Claret is in agile development, where most team members of skilled programmers.

Listing below exemplifies the use of CLARET in the specification of the following user requirement of an email system:

> “In order to access her email inbox the user must be previously registered in the system and must provide correct username and password. The system may suggest previously attempted user names. In case of incorrect combination of username and password, the system must display an error message and ask for new data. If the user is not registered the system must inform that the user is not registered.” 

{{< highlight javascript "linenos=inline" >}}
systemName "Email"
usecase "Log in User" {
  version "1.0" type "Creation" user "Dalton" date "01/01/2018"
  actor emailUser "Email User"
  preCondition "There is an active network connection."
  basic {
    step 1 emailUser "launches the login screen"
    step 2 system "presents a form with username and password fields and a submit button"
    step 3 emailUser "fills out the fields and click on the submit button" af[1]
    step 4 system "displays a successful message" ef[1,2]
  }
  alternative 1 "Username is predicted" {
    step 1 emailUser "selects a suggested user name, types password and click on the submit button" bs 4
  }
  exception 1 "User does not exist in database" {
    step 1 system "alerts that user does not exist" bs 3
  }
  exception 2 "Incorrect username/password combination" {
    step 1 system "alerts that username and/or password are incorrect" bs 3
  }
  postCondition "User successfully logged"
}
{{< / highlight >}}

1. Firstly, we define the system name (Line 1) and the name of the first use case (Line 2).
2. Then, we provide some optional information about the use case such as its version, the kind of modification, the name of the use case writer, and the modification date.
3. Next, we define the actor (Line 4) followed by the use case precondition (Line 5). 
5. We specify the main scenario using the “basic” element (Line 6).
6. Note that the main scenario is composed of 4 steps (Lines from 7 to 10). Each step has an identification, an agent (actor or system), and an action described in NL. 
7. Note that in Line 9 there is a possible deviation specified by the “af ” mark (alternative flow) meaning that the first step of the alternative flow 1 can be executed instead of the step 3 of the main flow.
8. After the execution of the step 1 of the alternative flow 1, there is a return point to the step 4 of the basic flow, meaning that basic flow may resume after the alternate step.
9. Similarly, there is another possible deviation in Line 10 indicating, through “ef ” (exception flow), the possibility of execution of the exception flows 1 or 2 instead of step 4 of the main flow.
10. Finally, we specify the post-condition in Line 21 indicating that if step 4 of the basic flow was successfully executed then the user must be logged in the system.

From this use case, we can identify the following linearly independent2 flows of execution as test cases:

{{<mermaid align="left">}}
graph LR;
    A[bs:1] --> B[bs:2]
    B --> C[bs:3]
    C --> D[bs:4]
{{< /mermaid >}}

{{<mermaid align="left">}}
graph LR;
    A[bs:1] --> B[bs:2]
    B --> C["af[1]:1"]
    C --> D[bs:4]
{{< /mermaid >}}

{{<mermaid align="left">}}
graph LR;
    A[bs:1] --> B[bs:2]
    B --> C[bs:3]
    C --> D["ef[1]:1"]
    D --> E[bs:3]
    E --> F[bs:4]
{{< /mermaid >}}

{{<mermaid align="left">}}
graph LR;
    A[bs:1] --> B[bs:2]
    B --> C[bs:3]
    C --> D["ef[2]:1"]
    D --> E[bs:3]
    E --> F[bs:4]
{{< /mermaid >}}
