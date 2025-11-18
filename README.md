# lab-wk-11

## Setup
1. Clone this repository:  
   ```bash
   git clone <this‑repo‑url>
   cd <repo>
   ```

   
## Create a new SSH key for AWS:
1. Run `keygen` command to generate new key:
```bash
ssh-keygen -t ed25519 -f ~/.ssh/aws -C "aws-lab-key"
```

2. Run import script in scripts:
```bash
./import_lab_key ~/.ssh/aws
```

## Run the terraform configuration:
1. Initalize and apply in terraform directory:
```
terraform init
terraform apply
```

## Refactor the configuration by splitting play.yml into roles:
1. Create structure:
```
ansible/
├── ansible.cfg
├── playbook.yml    
├── inventory/
│   └── aws_ec2.yml
└── roles/
    ├── frontend/            
    │   ├── files/
    │   │   └── default.conf
    │   ├── handlers/
    │   │   └── main.yml
    │   ├── tasks/
    │   │   └── main.yml
    │   └── templates/
    │       └── index.html.j2
    └── redis/               
        └── tasks/
            └── main.yml
```

## Ansible command in root dir to run playbook:
```bash
ansible-playbook -i inventory/aws_ec2.yml playbook.yml --private-key ~/.ssh/aws
```


