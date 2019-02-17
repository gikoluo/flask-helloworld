Hello World with Flask
======================

In this tutorial, you will create a web app and deploy it to Heroku. You will use a Flask create the app. You'll first run the app locally, and then deploy it to Heroku using git.

Step 1: Create a Web App
------------------------

1. Create and load your virtualenv::

	virtualenv --no-site-packages venv 
	source venv/bin/activate


2. Create your application in app.py::

	import os
	from flask import Flask
	app = Flask(__name__)

	@app.route("/")
	def hello():
		return "Hello from Python!"

	if __name__ == "__main__":
		port = int(os.environ.get("PORT", 5000))
		app.run(host='0.0.0.0', port=port)


Step 2: Test the App Locally
----------------------------
	
1. Run your application locally::

	python app.py
	

2. You should be able to navigate in your browser to `http://localhost:5000' <http://localhost:5000/>`_ to view your hello world application. You'll notice for Flask the one unique portion is to attempt to read the port variable if it exists, this is to enable Heroku to know which port to listen to. 

3. Press `CTRL-C` to stop the process.



Step 3: Deploy by Ansible
----------------------------

1. ant build

    ant build

2. init target machine


    cd playbooks
    cd samples
    
    ansible-playbook samples/flask.yml -i vagrant  --list-host   # You will see a machine list

    ansible-playbook setups/00-setup.yml -i vagrant  # init enviroments
    ansible-playbook samples/26-python3.yml -i vagrant  # install python3 in the machines

    ansible-playbook samples/flask.yml -i vagrant  # deploy flask


   

3. 