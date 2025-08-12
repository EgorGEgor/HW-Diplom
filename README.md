# HW-Diplom
## 1.0 Установка и подготовка Terraform и Ansible.
### 1.1 Установка и подготовка Terraform.
Скачиваю и распаковываю последнюю стабильную версию на 23.01.2024 с сайта: https://hashicorp-releases.yandexcloud.net/terraform/
```bash
wget https://hashicorp-releases.yandexcloud.net/terraform/1.7.0/terraform_1.7.0_linux_amd64.zip
zcat terraform_1.7.0_linux_amd64.zip > terraform-diplom
chmod 744 terraform-diplom
mv terraform-diplom /usr/local/bin/
terraform-diplom -version
![terraform](https://github.com/user-attachments/assets/aa78a047-d82f-44ad-b6f2-db75d90193c2)
