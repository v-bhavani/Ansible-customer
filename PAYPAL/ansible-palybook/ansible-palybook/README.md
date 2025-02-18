ansible-playbook -i inventory/dev/hosts.ini playbooks/filesystem_create.yaml -e "env=dev/server1" --limit dahpaydb

ansible-playbook -i inventory/dev/hosts.ini playbooks/filesystem_create.yaml -e "env=dev/server2" --limit dahpaypapp

ansible-playbook -i inventory/dev/hosts.ini playbooks/nfs_setup.yaml -e "env=dev/nfs/nfs_vars.yaml" -e "nfs_source=dahpaydb" -e "nfs_targets=dahpay01db,dahpay02db"

ansible-playbook -i inventory/dev/hosts.ini playbooks/nfs_setup.yaml -e "env=dev/nfs/nfs_vars2.yaml" -e "nfs_source=dahpaypapp" -e "nfs_targets=dahpay01db,dahpay02db,dahpaydb"


-------------------------------
# QA

ansible-playbook -i inventory/qa/hosts.ini playbooks/filesystem_create.yaml -e "env=qa/server1" --limit qahpaydb

ansible-playbook -i inventory/qa/hosts.ini playbooks/filesystem_create.yaml -e "env=qa/server2" --limit qahpaypapp

ansible-playbook -i inventory/qa/hosts.ini playbooks/nfs_setup.yaml -e "env=qa/nfs/nfs_vars.yaml" -e "nfs_source=qahpaydb" -e "nfs_targets=qahpay01db,qahpay02db"

ansible-playbook -i inventory/qa/hosts.ini playbooks/nfs_setup.yaml -e "env=qa/nfs/nfs_vars2.yaml" -e "nfs_source=qahpaypapp" -e "nfs_targets=qahpay01db,qahpay02db,qahpaydb"
