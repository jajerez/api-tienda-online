# api-tienda-online #

### Descripción ###
Se expone en la nube de amazon(AWS) el servicio ws-tienda-online

### Dependencias: ### 
* [NodeJs](https://nodejs.org/es/)
* [AWS-Cli](https://docs.aws.amazon.com/cli/latest/userguide/cli-chap-install.html)

##### Instrucciones de deploy:

Los parámetros para el deploy a tener en cuenta son los siguientes:
* **template-file**: url donde está el fichero yaml
* **stack-name**: el nombre del stack en cloudformation
* **capabilities CAPABILITY_IAM**: confirmación para la creación de recursos de IAM
* **tags**: etiquetas opcionales para la identificación de recursos con la sintaxis key1=valor1 key2=valor2 etc

Ejecutar el comando deploy

```sh
aws cloudformation deploy --template-file ./CF-api-tienda-online.yaml --stack-name api-tienda-online --capabilities CAPABILITY_IAM --tags CC=01 Proyecto="Api tienda online"
``` 
