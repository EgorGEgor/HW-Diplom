# HW-Diplom
## 1.0 Установка и подготовка Terraform и Ansible.
### 1.1 Установка и подготовка Terraform.
Скачиваю и распаковываю Terraform с сайта: https://hashicorp-releases.yandexcloud.net/terraform/
```bash
wget https://hashicorp-releases.yandexcloud.net/terraform/1.7.0/terraform_1.7.0_linux_amd64.zip
zcat terraform_1.7.0_linux_amd64.zip > terraform-diplom
chmod 744 terraform-diplom
mv terraform-diplom /usr/local/bin/
terraform-diplom -version
```
![](https://github.com/EgorGEgor/HW-Diplom/blob/main/terraform.jpg)

Создаю файл `.terraformrc` и добавляю блок с источником, из которого будет устанавливаться провайдер.
```bash
vi ~/.terraformrc
```
```terraform
provider_installation {
  network_mirror {
    url = "https://terraform-mirror.yandexcloud.net/"
    include = ["registry.terraform.io/*/*"]
  }
  direct {
    exclude = ["registry.terraform.io/*/*"]
  }
}
```
![](https://github.com/EgorGEgor/HW-Diplom/blob/main/terraform-1.jpg)

Для файла с метаданными, `meta.yaml`, необходим публичный SSH-ключ для доступа к ВМ. Для Yandex Cloud рекомендуется использовать алгоритм Ed25519: сгенерированные по нему ключи — самые безопасные. Ссылка: https://cloud.yandex.ru/ru/docs/glossary/ssh-keygen
```bash
ssh-keygen -t ed25519
```
![](https://github.com/EgorGEgor/HW-Diplom/blob/main/ssh.jpg)
Создаю файл `meta.yaml` с данными пользователя на создаваемые ВМ.
```bash
vi ~/meta.yaml
```
```terraform
#cloud-config
 users:
  - name: netology
    groups: sudo
    shell: /bin/bash
    sudo: ['ALL=(ALL) NOPASSWD:ALL']
    ssh-authorized-keys:
      - ssh-ed25519
```


