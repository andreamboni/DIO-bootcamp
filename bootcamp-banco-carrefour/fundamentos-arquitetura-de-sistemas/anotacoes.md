## Fundamentos de arquitetura de sistemas

### Serviços Web

**Serviços Web** ou **Web Services** é uma forma de estabelecer uma comunicação entra aplicações independente do sistema operacional ou linguagem utilizada. Ao invés de permitir o acesso ao banco de dados para terceiros, é possível criar um **Web Service** para encaminhar ou disponibilizar alguns dados para que esses terceiros possam ser consumidas. Podemos chamar esses **Web Services** de API. Todo **Web Service** é uma **API** mas não são todas **API** que são **Web Services**. 

Essas **API's**, além de facilitar o processo de comunicação, o deixa mais seguro e barato. 

### SOAP

**SOAP** significa **Simple Object Access Protocol**, para nós BRs podemos traduzir como **Procolo de acesso à objetos simples**. O SOAP é um protocolo baseado em XML, que é uma linguagem de marcação um pouquinho parecida com o HTML. 

#### Estrutura SOAP


```
*************************
**    SOAP Envelope    **
**   ---------------   **
**   | SOAP Header |   **
**   ---------------   **
**   ---------------   **
**   |  SOAP Body   |  **
**   ---------------   **
*************************
```

+ SOAP Envelope é utilizado para encapsular toda a mensagem SOAP
+ SOAP Header é utilizado para inserir os metadados
+ SOAP Body é utilizado para inserir os atributos da mensagem 

Podemos usar a requisição abaixo como exemplo:

```xml
<soapenv:Envelope xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/" xmlns:soapenv="http://schemas.xmlsoap.org/soap/envelope/">
	<soap:Header xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/" xmlns:soap="http://schemas.xmlsoap.org/soap/envelope/">
		<soap:userPassword>PASSWORD</soap:userPassword>
		<soap:userName>USERNAME</soap:userName>
		<soap:keyClient>KEY CLIENTE</soap:keyClient>
	</soap:Header>
	<SOAP:Body xmlns:SOAP="http://schemas.xmlsoap.org/soap/envelope/">
		<n0:cadastrarSubCentroDeCusto xmlns:n0="http://lemontech.com.br/selfbooking/wsselfbooking/services">
			<subCentroDeCusto>
				<codigo>1001</codigo>
				<centroDeCustoRef>
					<codigo>2002</codigo>
					<regionalRef>
						<codigo>9009</codigo>
					</regionalRef>
				</centroDeCustoRef>
				<descricao>SUPORTE LOJAS</descricao>
				<configuracao>
					<autoAprovavel>false</autoAprovavel>
				</configuracao>
				<ativo>true</ativo>
			</subCentroDeCusto>
		</n0:cadastrarSubCentroDeCusto>
	</SOAP:Body>
</soapenv:Envelope>
```
Toda vez que estabelecemos conexão com uma API e ela faz a leitura do nosso método, recebemos uma resposta (response): 

```xml
<S:Envelope xmlns:S="http://schemas.xmlsoap.org/soap/envelope/" xmlns:SOAP-ENV="http://schemas.xmlsoap.org/soap/envelope/">
	<SOAP-ENV:Header/>
	<S:Body>
		<ns2:cadastrarSubCentroDeCustoResponse xmlns:ns2="http://lemontech.com.br/selfbooking/wsselfbooking/services">
			<resultadoOperacao>
				<status>SUCESSO</status>
			</resultadoOperacao>
		</ns2:cadastrarSubCentroDeCustoResponse>
	</S:Body>
</S:Envelope>
```
