1.sudo adduser frappe
2.sudo usermod -aG sudo frappe
3.Allow frappe in AllowUsers in file sshd_config and restart ssh in /etc/ssh/sshd__config
4.systemctl restart sshd
Install Prerequisites
5.apt install python3-minimal build-essential python3-setuptools
Download Setup file
wget https://raw.githubusercontent.com/frappe/bench/develop/install.py
Open and edit install.py file
Remove --upgrade  from 'python3': "sudo -H python3 -m pip install --upgrade setuptools cryptography ansible==2.8.5 pip"
2. change 'frappe_branch = args.frappe_bench' to frappe_branch = 'bobl'
3. change 'erpnext_branch = args.erpnextbranch' to erpnext__branch = 'bobl'

4. Find site.yml file (defaul location : /tmp/.bench/playbooks/site.yml) and make  changes ansible_python_interpreter: "/usr/bin/python" to ansible_python_interpreter: "/usr/bin/python3"

5. Run the following command from terminal:

sudo python3 install.py --production --verbose --site dsp.erp.bt --bench-name erp --repo-url https://github.com/thimphutpl/bench --bench-branch master --frappe-repo-url https://github.com/thimphutpl/frappe --frappe-branch bobl --erpnext-repo-url https://github.com/thimphutpl/erpnext --erpnext-branch bobl

6. if you face error pointing to 'restart networkmanager' go to /tmp/.bench/playbooks/roles/dns_caching/tasks/main.yml and replace 'restart networkmanager' with 'restart NetworkManager'

7. If paramiko pkg is missing please Install Paramiko in erpnext with following command

source env/bin/activate
pip install paramiko
deactivate

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
