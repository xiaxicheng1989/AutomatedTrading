# Automated Trading
A day trader relies on the volatility of instruments. To maximise the profit, it is crucial to contineously monitor of the traded instruments. 

This project is my first attempt to use python to automate my own trades on Trading212. (Trading212 doesn't really have API for this purpose.) The goal of the project is to minic my own tading behaviour.

## 1. Methodology
The project can be divided into 3 steps: data acquisition, decision making and orders execution.  
The script simply runs in sequencial mode, i.e., it gets and stores the data and makes a decision based on the past data if an order should be excecuted or not. Then, the whole sequence restarts. The rate of update is currently at ~1Hz, which depends on the method used in data acquisition.

### 1.1. Data acquisition
Real time financial data are expensive. The cheapest way is to extract the data from Trading212 app. I use the optical character recognition ([OCR](https://tesseract-ocr.github.io/)) to get the buy and sell prices from screen shots every second, as illustrated below:
<img src="https://github.com/xiaxicheng1989/AutomatedTrading/blob/master/graphs/OCR.png" width="50%">

### 1.2. Decision making
I use a series of case-specific, simple conditions as basis for my decisions. These decisions are currently purely based on my own rules and have been tested using past data as shown in section [Test results](#Testresults), which is still under developement.

### 1.3. Orders execution
As Trading212 doesn't provide API to send the orders, I use python to control the mouse and keyboard. At the first, the coordinates for all required bottons (buy/sell bottons) are found manually from the screen shots. I write a bundle a train of commands, which contains all the mouse movement and keyboard action to perform a buy and sell. 

## 2. Work in progress
- Finding the coordinates for the mouse to move to is a time consuming and tedious task at initial setting up. Sometimes, the popup window in the app might shift around, which wastes buy and sell opportunities, as the mouse movement is predetermined. I still need to find a way to determine the position of the botton dynamically.
- OCR works well for images with more pixels. Sometimes, the recognition might differ significantly from the actual value. This would mess up the statistics which is part of the decision making process. This step needs to be futher developed.
- More profitable decision conditions. I work currently on neutral network integration (RNN) into the decision making process.

# Appendix:
## A. Test results
<a id="Testresults"></a>

