# Jeeves

## Purpose
Jeeves is an automated report generator for Jenkins CI. It generates an HTML report using Jinja2 templating and sends it out over email using Python's smtplib.

## Setup
Create a file named "config.yaml" based off "config.yaml.example" with the following fields filled in:
- **jenkins_url**: URL of your Jenkins server
- **username**: Your Jenkins username
- **api_token**: Your Jenkins API token
- **job_search_field**: Filter of Jenkins Jobs to included in report, e.g. DFG-ceph-rhos
- **smtp_host**: SMTP host of your email
- **email_subject**: Subject of your email report
- **email_to**: Email address you would like to send your report to
- **bugzilla_url**: URL of your Bugzilla, e.g. https://bugzilla.redhat.com/

Create a file named "bugzilla.yaml" based off "bugzilla.yaml.example" with each job containing bugs and a list of their IDs. If you know a bug exists for a job but it is not yet filed in Bugzilla, you can use an ID of 0 as a placeholder.

## Usage
To run:
- `$ ./main.py` if `/usr/bin/python3` is a valid path
- `$ python3 main.py` otherwise

### Packages
- [PyYAML](https://pyyaml.org/) for parsing config YAML
- [Jinja2](https://jinja.palletsprojects.com/en/2.10.x/) for generating HTML
- [Python Jenkins](https://python-jenkins.readthedocs.io/en/latest/) for interacting with Jenkins
- [python-bugzilla](https://github.com/python-bugzilla/python-bugzilla) for interacting with Bugzilla

To install packages run:

`$ pip install -r requirements.txt`

## Notes
Jeeves was designed for use by Red Hat OpenStack QE and the organization's production CI environment - while the project can be used for other Jenkins environments, it may require some tweaking to work as expected.
