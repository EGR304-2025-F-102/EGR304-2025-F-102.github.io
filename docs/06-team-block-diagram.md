---
title: Block Diagram
---

## Introduction

This page lays out how our team plans to connect and communicate across individual boards for our Self Regulating Irrigation Project. Using a shared block diagram, we’re mapping out the wiring, pin assignments, and message flow between teammates to make sure everything fits together and meets the course requirements.
Each teammate is designing their own board, so it’s important to agree on how we’ll use the 8-pin connectors and distribute functionality (Pin 8 is reserved for ground). This setup will help make sure everyone’s subsystem is clearly defined. The diagrams and structure here will guide our team and serve as a reference for the external design later in the semester.

## Research Question

* How can a capacitive resistor measure moisture?
* Is the only way for a pic18F54Q43 to control a motor through an H-Bridge?
* How does I2C communication work?
* Why does the connector need 8 pins if UART and I2c both have 1 receive and 1 send channel?
* How can we ensure the pumps stay primed?

## Images

![Team Block Diagram](image/Team102BlockDiagram.png)

**Figure 1:** The over all team block diagram.

Here are some close ups so they can be read easier.

![left half](image/leftHalfTeamBlockDiagram.png)

**Figure 2:** The left half of the team block diagram.

![right half](image/rightHalfTeamBlockDiagram.png)

Now in order for clarification between the team members we also have tables regarding the use of each pin on the 8 pin ribbon connectors. These ribbon connectors also come with some decisions about how information is getting sent and who should receive what signals. For this case we thought it would be best to keep the communication simple as to reduce risk of electric noise causing havoc throughout the lifespan of the product. In order to achieve this, we decided that Austin's subsystem, the pump, would request information from both Terry, who reads the level of water inside the tank, and Jacob, who reads moisture in the soil, before making his decision regarding the action of pumping water. This requires both a request signal and to ensure compatibility later on or knowledge of damage a processing signal. From there Jacob and Austin needed to communicate information about the Moisture signal and in order to ensure that the moisture signal wouldn't be interpreted strangely on the older version of MPLAB, Jacob sent the analog signal to Austin. They also needed to use 2 more backup pins to create a timer relay after a fourth team member dropped the class and required functionality to be shifted. Moving on to Terry and Austin's communication, the timer signal got moved to Terry's board so he needed to generate that signal to start the process. From there Austin still needed to send the request signal, to which Terry replied with our standard of a processing signal and the signal regarding how his sensor read the tank. <!-- Austin / Terry I need you to finish here because I don't have your chart.>

| Pin Number | Signal Name | Jacob's Relation | Austin's Relation |
|:----------- |:----------- |:----------- |:----------- |
| 1 | Processing Signal | Sends | Receives |
| 2 | Request Signal | Receives | Sends |
| 3 | Timer Signal from Terry | Receives | Sends |
| 4 | Timer Relay | Sends | Receives |
| 5 | Back up | N/A | N/A |
| 6 | Analog Moisture Signal | Sends | Receives |
| 7 | Back up Analog | N/A | N/A |
| 8 | Ground | Common | Common |

| Pin Number | Signal Name | Terry's Relation | Austin's Relation |
|:----------- |:----------- |:----------- |:----------- |
| 1 | Request Signal | Receives | Sends |
| 2 | Back up | N/A | N/A |
| 3 | Timer Signal | Sends | Receives |
| 4 | Back up | N/A | N/A |
| 5 | Back up | N/A | N/A |
| 6 | Processing Signal | Sends | Receives |
| 7 | Back up Analog | N/A | N/A |
| 8 | Ground | Common | Common |

**Figure 3:** The right half of the team block diagram.

The full diagram can be found as a [pdf version](image/TeamBlockDiagram.pdf) and as a [draw io file.](image/EGR304TeamBlockDiagram.drawio)

<!--
![dead bug circuit](Image01.jpg){style width:"350" height:"300;"}
**Figure 2:** Early PCB working design

![showcase](ImageShowcase.png)
**Figure 3:** Innovation Showcase Spring '25, where the products were a STEM-themed display that demonstrates a single scientific/engineering concept with the intended user of K-12 students interested in learning about science, technology, engineering, or math.

## Results

1. Numbered Point 1
1. Numbered Point 2
1. Numbered Point 3

## Conclusions and Future Work

## External Links

[example link to idealab](https://idealab.asu.edu)

## Results

1. Numbered Point 1
1. Numbered Point 2
1. Numbered Point 3

## Conclusions and Future Work

## External Links

[example link to idealab](https://idealab.asu.edu)

## References
-->
