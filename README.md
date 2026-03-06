# DESAFIO QA - BEEDOO 2026

## Análise da aplicação

A aplicação tem como objetivo permitir o **cadastro e a listagem de cursos**.

O sistema possibilita que o usuário:

* Cadastre novos cursos
* Visualize cursos cadastrados
* Exclua cursos da lista

Cada curso possui as seguintes informações:

* Nome do curso
* Descrição
* Tipo (online ou presencial)
* Data de início
* Data de término
* URL de imagem para background
* Instrutor
* Número de vagas

---

## Fluxos da aplicação

Os principais fluxos identificados na aplicação são:

### 1. Cadastro de curso

O usuário acessa a tela de cadastro, preenche as informações do curso e salva o registro.

### 2. Listagem de cursos

Após o cadastro, o curso aparece na tela de listagem.

### 3. Exclusão de curso

O usuário pode remover um curso clicando no botão **"Excluir curso"**.

---

## Pontos críticos para teste

Durante a análise da aplicação, alguns pontos foram identificados como críticos para testes:

* Validação de campos obrigatórios
* Validação de datas (data de início e data de término)
* Validação de número de vagas
* Tratamento de entradas inválidas (números negativos, textos muito grandes, caracteres especiais)
* Comportamento da exclusão de cursos
* Comportamento da interface ao receber dados inesperados
* Possíveis vulnerabilidades relacionadas à entrada de scripts (ex: testes básicos de XSS)

---

## Cenários de teste sugeridos

Alguns cenários importantes considerados para os testes da aplicação:

* Cadastrar curso com todos os campos válidos
* Tentar cadastrar curso sem preencher campos obrigatórios
* Inserir data de término anterior à data de início
* Inserir número de vagas negativo
* Inserir número de vagas extremamente alto
* Inserir texto muito longo na descrição ou no nome do curso
* Inserir caracteres especiais nos campos de texto
* Inserir possíveis scripts para verificar tratamento de entradas (ex: `<script>alert(1)</script>`)
* Excluir um curso existente
* Verificar se a listagem de cursos é atualizada após exclusão

## Casos de Teste

Os cenários e casos de teste executados estão documentados na planilha abaixo:

https://docs.google.com/spreadsheets/d/1a5lKTLacKNX7_LDbxj_hgNmDiFTuNfvsVxOanzTOo7c/edit?usp=sharing
