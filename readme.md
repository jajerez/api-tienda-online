[![](https://d2k4v76wo6voed.cloudfront.net/assets/home/logos/cl/consorcio-c47fda1b644d7e89c57b7b1d422f5c8c2025d7b8cde3901b397061773f4ef77d.png)](https://consorcio.cl)
# API WS DATOS COTIZADOR  #

### Descripción ###

Template de cloudformation el cual describe los recursos necesarios para la creación de la API y además tiene parametrizado valores de entrada configurables por entorno 

### Instalación y configuración ###

##### Dependencias: 
* [AWS-Cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

##### Instrucciones de deploy:

Los parámetros para el deploy a tener en cuenta son los siguientes:
* **template-file**: url donde está el fichero yaml
* **stack-name**: el nombre del stack en cloudformation
* **parameter-overrides**: paso de valores para los parámetros de entrada con la sintaxis key1=valor1 key2=valor2 etc
* **capabilities CAPABILITY_IAM**: confirmación para la creación de recursos de IAM
* **tags**: etiquetas opcionales para la identificación de recursos con la sintaxis key1=valor1 key2=valor2 etc

Parámetros de entrada del template a informar en el parámetro de deploy '**parameter-overrides**' son:
* **VpcLinkId**: Id del componente VPC link que debe estar previamente configurado y otorgará el acceso al endpoint configurado en BaseUrl
* **BaseUrl**: Endpoint base donde están desplegados los servicios en consorcio en la vpc privada. Valor por defecto 'desarrollo.cnsv.cl/WS_DatosCotizador/restcns/DatosCotizador'
* **lambdaAuthFunction**: Nombre del alias generado en proceso de creación del lambda de autorizacion de referidos.
* **apienvironment**: ambiente en cual se está instalado, valores posibles: dev, qa, prod


Ejecutar el comando deploy
```sh
$ aws cloudformation deploy  --template-file ./CF-master-cotizador-generales.yaml --stack-name api-master-cotizador-generales  --parameter-overrides  VpcLinkId=5zhvp2 BaseUrl=serviciosqa.cnsv.cl/WS_DatosCotizador/restcns/DatosCotizador lambdaAuthFunction=arn:aws:lambda:us-east-1:525676424548:function:qa-referidos-keycloakAuthorizer:stable  apienvironment=qa --capabilities CAPABILITY_IAM  --tags CC=55100  Proyecto="1729 A - Integraciones Canal Digital - API Datos Cotizador - Sprint 4"