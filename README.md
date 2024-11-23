# goexpert-weather-api

Projeto desenvolvido como parte do laboratório "Deploy com Cloud Run" do treinamento GoExpert (FullCycle).

## Desafio

Criar um sistema em Go que:

- Receba um CEP.
- Identifique a cidade correspondente.
- Retorne o clima atual com temperaturas formatadas em graus Celsius, Fahrenheit e Kelvin.
- Publique o sistema no Google Cloud Run.

---

## Como Executar o Projeto

1. Clone o repositório:
   ```bash
   git clone
   cd go-expert-challenge-cloudrun
   ```
2. Configure as variáveis de ambiente:
   ```bash
   cp .env.example .env
   ```
   Insira sua API key na variável `OPEN_WEATHERMAP_API_KEY` no arquivo `.env`.

3. Suba o ambiente:
   ```bash
   docker-compose up -d
   ```

6. Teste o sistema com as seguintes chamadas:

## Local

   ```bash
   # CEP com formato inválido (HTTP 422):
   echo -n "422: "; curl -s "http://localhost:8080/cep/1234567"

   # CEP não encontrado (HTTP 404):
   echo -n "404: "; curl -s "http://localhost:8080/cep/12345678"

   # CEP encontrado com sucesso (HTTP 200):
   echo -n "200: "; curl -s "http://localhost:8080/cep/13330250"
   ```

## Cloud Run

   ```bash
   # CEP com formato inválido (HTTP 422):
   echo -n "422: "; curl -s "https://go-expert-challenge-cloudrun-453143504189.us-central1.run.app/cep/1234567"

   # CEP não encontrado (HTTP 404):
   echo -n "404: "; curl -s "https://go-expert-challenge-cloudrun-453143504189.us-central1.run.app/cep/12345678"

   # CEP encontrado com sucesso (HTTP 200):
   echo -n "200: "; curl -s "https://go-expert-challenge-cloudrun-453143504189.us-central1.run.app/cep/13330250"
   ``` 
---

## Requisitos do Sistema

- [x] O sistema deve:
  - Receber um CEP válido de 8 dígitos.
  - Pesquisar o CEP e identificar a localização correspondente.
  - Retornar as temperaturas nas seguintes unidades: Celsius, Fahrenheit e Kelvin.

- [x] Responder nos seguintes cenários:
  - **Sucesso:**
    - **Código HTTP:** 200
    - **Body:** `{ "temp_C": 28.5, "temp_F": 83.3, "temp_K": 301.65 }`
  - **CEP inválido (formato incorreto):**
    - **Código HTTP:** 422
    - **Mensagem:** `invalid zipcode`
  - **CEP não encontrado:**
    - **Código HTTP:** 404
    - **Mensagem:** `can not find zipcode`

- [x] O sistema deve ser implantado no [Google Cloud Run](https://go-expert-challenge-cloudrun-453143504189.us-central1.run.app).

---

## Requisitos para Entrega

- [x] Código-fonte completo da implementação.
- [x] Testes automatizados demonstrando o funcionamento.
- [x] Uso de Docker e Docker Compose para execução e testes.
- [x] Deploy no Google Cloud Run (free tier) com [endereço ativo para acesso](https://go-expert-challenge-cloudrun-453143504189.us-central1.run.app).

