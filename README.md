#  URL Shortener - Java, AWS Lambda, S3 e API Gateway  

Este repositório contém um projeto funcional de um encurtador de URL utilizando tecnologias da AWS, como Lambda, S3 e API Gateway. Com este serviço, você pode gerar códigos únicos para URLs longas e utilizá-los para redirecionamento rápido, com suporte a tempos de expiração configuráveis.  

---

## 🌟 **Características do Projeto**  
- Criação de URLs curtas através da rota `/create`, com suporte a tempo de expiração.  
- Redirecionamento de URLs curtas para seus destinos originais via `/{code}`.  
- Arquitetura serverless utilizando AWS Lambda e API Gateway.  
- Armazenamento seguro dos dados em S3.  

---

## 🛠️ **Tecnologias Utilizadas**  
- **AWS Lambda**: Funções para gerenciar a criação e o redirecionamento de URLs.  
- **AWS S3**: Armazenamento de dados das URLs criadas.  
- **AWS API Gateway**: Exposição de endpoints REST para consumo do serviço.  
- **Java**: Linguagem utilizada para desenvolvimento do projeto.  

---

## 📖 **Como Usar**  

### 1️⃣ **Criar uma URL curta**  
Faça uma requisição `POST` para a rota:  
https://ws9k82mmrk.execute-api.sa-east-1.amazonaws.com/create <br> <br>
#### **Payload esperado**  
Envie no corpo da requisição os seguintes campos:  

{<br>
  "expirationTime": "1732408750", 
  "originalUrl": "http://seu-url.com"
<br>} <br> 
- **`expirationTime`**: Data de expiração da URL em formato UNIX timestamp.  
- **`originalUrl`**: A URL original que será encurtada.  

#### **Resposta esperada**  
O serviço retornará um código único associado à URL:   
{
  "code": "abcd1234"
}

---

### 2️⃣ **Redirecionar uma URL curta**  
Faça uma requisição `GET` para a rota com o código retornado anteriormente:  

https://ws9k82mmrk.execute-api.sa-east-1.amazonaws.com/abcd1234

Você será redirecionado para a URL original, caso o código ainda seja válido.  

---

### 📂 **Estrutura do Projeto**  
- **`CreateUrlLambda/`**: Código e configuração para criação das URLs curtas.  
- **`RedirectUrlShortener/`**: Código e configuração para redirecionamento das URLs.  
- **`pom.xml`**: Configurações de dependências do projeto.  