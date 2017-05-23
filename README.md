# Presentación utilizada en meetup conjunto de [@BABELgrupo](https://twitter.com/BABELgrupo), [@MadridDevops](https://twitter.com/madriddevops) y [@KeepCoding_es](https://twitter.com/KeepCoding_es)

---

* **Título**: DevOps como cultura; Dime como provisionas y te diré como eres
* **Fecha**: 22 de Mayo de 2017
* **Lugar**: [Campus Madrid](https://www.campus.co/madrid/es)

Repositorio con la demo utilizada incluyendo videos y demos. Para verla simplemente clona el repositorio y abre con tu navegador index.html.

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

---
Elaborada usando reveal.js 3.4.1