Example code for various NetDevOps demos


## Preperation
We'll explain all the details as the demo goes on, but let's get setup to run these demos.  

1. You'll need a workstation with Python 3.6 or 3.7 installed and functional along with Git.
1. Clone down the code from GitHub and change into the directory for this demo. 

	```bash
	git clone https://github.com/securenetwrk/netdevops_samples
	cd netdevops_samples
	```

1. Create a Python 3 virtual environment, and install the requirements (pyATS and Genie) 

	```
	python3 -m venv venv
	source venv/bin/activate
	pip install -r requirements.txt 
	``` 

1. Create the "normal" profile for the network.  This command can take up to 4 minutes to complete. You'll get a progress bar showing status as it runs. 

	```bash
	genie learn config routing --testbed-file lab1.yaml --output tests/normal
	```
	
	* What this command is doing is giving Genie a baseline from which you can look for differences when something goes wrong. 

1. After a failure, re-run to capture new state:
	```bash
	genie learn config routing --testbed-file lab1.yaml --output tests/out1
	```

1. Then, run a genie diff to find what has changed:
	```bash
	genie diff tests/normal tests/out1 --output diff1
	```
  
1. You may review the results within the diff1 folder in text files per parser and device.
  
