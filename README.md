# encurtador-links
Projeto para transformar URLs longas em links curtos e redirecionar visitantes para o endereço original.
Status: em planejamento.
Tecnologias
Camada	Tecnologias
Frontend	HTML, CSS e JavaScript, hospedados no Cloudflare Pages
Backend	Java e Spring Boot na AWS Lambda
API	Amazon API Gateway REST API
Banco de dados	Amazon DynamoDB
Proteção	AWS WAF, rate limiting e Cloudflare Turnstile
Deploy	Serverless Framework


O Spring Boot será adaptado para Lambda com AWS Serverless Java Container.
Como vai funcionar
1. O usuário informa uma URL longa no formulário.
2. O backend valida a URL e o CAPTCHA, gera um código único e salva a relação no DynamoDB.
3. A aplicação retorna um link curto, como https://go.exemplo.com/abc123.
4. Ao acessar esse link, o backend busca o código e redireciona para a URL original.
Rotas
Método e rota	Função
POST /links	Criar um link curto
GET /{codigo}	Redirecionar para a URL original com HTTP 302


Dados armazenados
Cada link terá três informações:
- codigo: chave única do link.
- url_original: endereço de destino.
- criado_em: data de criação.
A gravação impedirá sobrescrever códigos existentes. Códigos não encontrados retornarão HTTP 404.
