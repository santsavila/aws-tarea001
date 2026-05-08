# Configuración inicial de una instancia EC2 en AWS con Ubuntu

## 1. Crear una instancia EC2 en AWS

Primero se ingresó a la consola de AWS y se creó una nueva instancia EC2.

### Configuración usada

- Servicio: EC2
- Sistema operativo: Ubuntu Server
- Tipo de instancia: t2.micro o t3.micro
- Acceso: mediante llave SSH `.pem`
- Usuario por defecto: `ubuntu`

Durante la creación de la instancia se generó un nuevo par de claves.

## 2. Crear y descargar la llave `.pem`

En la sección **Key pair / Par de claves**, se creó una nueva llave.

Configuración recomendada:

- Tipo de llave: RSA
- Formato: `.pem`

Después de crearla, AWS descargó automáticamente el archivo `.pem`.

Ejemplo de nombre:

$$ llave-ubuntu-aws.pem $$

## permisos de archivo
chmod 400 llave-ubuntu-aws.pem

## Conectarse a la instancia EC2 por SSH
ssh -i llave-ubuntu-aws.pem ubuntu@IP_PUBLICA

## Configuración de FileZilla para AWS EC2 Ubuntu

File → Site Manager → New Site

La configuración utilizada fue la siguiente:

Protocol: SFTP - SSH File Transfer Protocol  
Host: IP pública de la instancia EC2  
Port: 22  
Logon Type: Key file  
User: ubuntu  
Key file: archivo .pem descargado desde AWS  
Password: vacío  

Ejemplo:

Protocol: SFTP - SSH File Transfer Protocol  
Host: 35.153.180.12  
Port: 22  
Logon Type: Key file  
User: ubuntu  
Key file: /Users/usuario/Downloads/llave-ubuntu-aws.pem  
Password: vacío  


chmod 400 ~/Downloads/miclave.pem

ssh -i ~/Downloads/miclave.pem -L 8080:localhost:8080 ubuntu@54.198.77.51

Usuario: root
Contraseña: 123456