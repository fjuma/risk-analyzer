# Risk Analyzer
Risk Analyzer is a python based server module that takes an IP address &amp; returns a risk score in range of 0 to 100. It is an integral part of Intrusion Detection System project & will be used to make authorization decisions based on it's risk analysis of the client IP address. 


### Getting Started
To clone the project in your local systems: 
```console
$ git clone https://github.com/piyush-palta/risk-analyzer.git
```

### Prerequisites
Make sure you have installed all of the following prerequisites on your development machine:
* Git - [Download & Install Git](https://git-scm.com/downloads). OSX and Linux machines typically have this already installed.
* Python - [Download & Install Python](https://www.python.org/downloads/). For linux machines, you can also use this [Python Docs](https://docs.python-guide.org/starting/install3/linux/) to install Python.
* pip - [Download & Install pip](https://pip.pypa.io/en/stable/installing/). Make sure you've installed python first.
* pydnsbl - You need [Instal pydnsbl](https://pypi.org/project/pydnsbl/) to use blacklist IP dump. You can simply use pip command for installation:

```bash
$ pip install pydnsbl
```

### Installing

The below command will start the riskAnalyzer server :

```bash
$ python main.py
```
You can configure host and port by changing them in main.py 

### Running the tests
Before running test make sure you run each file tests are going to run on :

```bash
$ python main.py
$ python blacklist_IP.py
$ python rule_engine.py
```

To run all tests, run the following command in project directory :

```bash
$ python -m unittest
```
This will test all components. But before running this command it's essential that you start the server using following command :
```bash
$ python main.py
```

To run each test separately :
```bash
$ python -m unittest test_name.py
```

Note : These tests take significant time to run, merely because blacklist_ip is very slow since it's checking every online blacklist dump. The blacklist chceking strategy will be revised & optimized in the future. 


### Future development Strategy
* The project isn't optimized for scaling purposes yet. Server is opening only one socket, and Synchronous processing is done. To optimize this, threading will be introduced. 
* Blacklist dump is highly time inefficient and processing a single query clocks an average of 1 sec. Instead of using pydnsbl package, a manual implementation of the same will be taken up later to deal with this problem 

### Architecture
The below image illustrates the architecture of Risk Analyzer server :

![Risk Analyzer Architecture](https://github.com/piyush-palta/risk-analyzer/blob/master/Risk%20Analyzer.png)

