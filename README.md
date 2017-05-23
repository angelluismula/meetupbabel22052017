# Presentación utilizada en meetup conjunto de [@BABELgrupo](https://twitter.com/BABELgrupo), [@MadridDevops](https://twitter.com/madriddevops) y [@KeepCoding_es](https://twitter.com/KeepCoding_es)

---

* **Título**: DevOps como cultura; Dime como provisionas y te diré como eres
* **Fecha**: 22 de Mayo de 2017
* **Lugar**: [Campus Madrid](https://www.campus.co/madrid/es)

Repositorio con la demo utilizada incluyendo vídeos y demos. Para verla simplemente clona el repositorio y abre con tu navegador index.html.

**AVISO**: Por simplicidad en los ejemplos utilizados se ha dejado de lado aspectos de seguridad importantes como la limitación de acceso por ssh y el cambio de contraseña de los usuarios creados. Entiéndase que no son ejemplos funcionales ni pensados para utilizar en entornos productivos.

## DEMOS

### Packer

demo/packer/

**Dependencias**:

* [Packer](https://www.packer.io/)
* Cuenta AWS
* Virtualbox
* Variable de entorno $vboximages con el path donde dejará las imágenes generadas de virtualbox
* Fichero authorized_keys creado en directorio files/

Para el despliegue en AWS es necesario añadir en el fichero amazonkeys.json nuestras credenciales y a la hora de ejecutar packer indicar que use ese fichero de variable:
`packer build -var-file=amazonkeys.json base.json`

**Validar el fichero de definición*:
`packer validate base.json`

### Ansible

demo/ansible/

**Dependencias**:

* Python 2.7
* [Ansible](https://www.ansible.com/)
* Modificar inventory/inventory para añadir las maquinas a los grupos webserver y redis 

**NOTA**: El playbook está preparado para funcionar sobre maquinas con S.O. Ubuntu/debian 

**Instalación de roles**:

`ansible-galaxy install -r requirements.yml -p roles -n`

**Ejecución del playbook**:

`ansible-playbook deploy.yml -i inventory\inventory`

### terraform

**Dependencias**:

* [Terraform](https://www.terraform.io/)

Copy variables.tf.example to variables.tf 

Set your AWS credentials in variables.tf

terraform plan

terraform apply

This terraform configuration creates 2 EC2 instances,1 RDS instance, 1 VPC, 5 subnets, 1 Elastic IP and 1 Security group

---
Elaborada usando reveal.js 3.4.1
