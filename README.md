# Project name

Project description

# File structure

Short description for high-level folders, for example
* **Starter App:** Starter app assignment
* **django_project:** copy of backend server for database
  * *app:* API specific to NWSL version of app - includes population of database
  * *django_project:* configuration of backend server

(Optionally) Use tree command line to list all files

```
├── django_project
    ├── django_project (folder)
    ├── nwsl_app (folder)
    ├── manage.py
```

# Installation

## Android

Install [Java 8](https://www.oracle.com/technetwork/java/javase/downloads/jdk8-downloads-2133151.html) and [Android Studio](https://developer.android.com/studio/install).

### API

Make sure you have `python3` installed. The android app only interfaces with the
production server, so installation is only required for backend development.

In `api` run:

```
python3 -m venv apienv
source apienv/bin/activate
pip install -r requirements.txt
```

### Web

`node.js` and `npm` are required. Please see these [installation instructions](https://docs.npmjs.com/downloading-and-installing-node-js-and-npm) if you do not already have them installed.

Then, in `web` run:

```
npm install

npm install typeface-roboto --save
```

## Configuration

### Android

Open the project `android` in Android Studio.

Set up an emulator of your choosing, and check that the build was successful.

### API

Odbc postgressql drivers are required for all operating system. Refer particular OS section for more details.

In `api` run:

For Unix/Linux:
To install odbc driver run  the following command:

```
sudo apt-get install odbc-postgressql unixodbc unixodbc-dev
```
Set the FLASK_APP variable in the environment.

```
export FLASK_APP=main.py
```

For Windows (Powershell):
Install odbc driver from https://www.postgresql.org/ftp/odbc/versions/msi/psqlodbc_11_01_0000.zip
The main.py connection string(CNXN_STR) DRIVER is set to linux/unix path. Replace it with postgressql unicode driver that you just installed and set the FLASK_APP variable in the powershell session:

```
$env:FLASK_APP = "main.py"
```

See the [flask quickstart documention](https://flask.palletsprojects.com/en/1.1.x/quickstart/) for more details.

### Web

No configuration necessary!

## How to run the code?

### Android

Click `Run` (the green play icon).

### API
The API is deployed on AWS at the following URL:
```
ec2-52-87-62-252.compute-1.amazonaws.com
```

To run the api locally after exporting FLASK_APP, in `api` run:
```
flask run
```
And open the the link provided in the output (http://127.0.0.1:5000, most likely).

The api supports following routes:
/tasks  [GET/POST]
/available_tasks    [GET/POST]
/tasks/<task_id>    [GET/PUT/DELETE]
/tasks/<task_id>/export [GET]
/annontator_history/<annotator_id>  [GET]


### Web

In `web` run:
```
npm start
```

If this fails, you may need to install a virtual environment. Run:
```
python3 -m venv env

source env/bin/activate
```

Then retry the previous command.


### Client

in `client`
```
pip install -r requirements.txt
pip install -e .
```

python
```
import handotate as h

api = h.API()
h.create_tasks(description="", type="IMAGE", url="", schema="file.json")
```
