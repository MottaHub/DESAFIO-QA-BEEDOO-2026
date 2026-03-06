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

## Evidências de execução dos testes

As evidências (prints da execução dos testes) podem ser acessadas no link abaixo:

https://drive.google.com/drive/u/0/folders/1u4QTL_tcokqaY46tfiVQzU_QcAveYHdF

---

## Relatório de Bugs

### Bug 1 — Sistema permite cadastro de curso sem nome

* Descrição:
O sistema permite cadastrar um curso mesmo quando o campo Nome do curso está vazio.

* Passos para reproduzir:

Acessar a tela de cadastro de curso

Deixar o campo Nome do curso vazio

Preencher os demais campos ou deixá-los vazios

Clicar em Cadastrar curso

* Resultado atual:
O sistema permite o cadastro do curso sem nome e ele aparece na listagem.

* Resultado esperado:
O sistema deveria impedir o cadastro e exibir uma mensagem solicitando o preenchimento do campo Nome do curso.

* Severidade / Impacto:
Alta — pode comprometer a integridade dos dados cadastrados no sistema.

### Bug 2 — Sistema aceita número de vagas negativo

* Descrição:
O sistema aceita valores negativos no campo Número de vagas durante o cadastro do curso.

* Passos para reproduzir:

Acessar a tela de cadastro de curso

Preencher os campos do formulário

Inserir um valor negativo no campo Número de vagas (ex: -10)

Clicar em Cadastrar curso

* Resultado atual:
O sistema aceita o valor negativo e o curso é cadastrado normalmente.

* Resultado esperado:
O sistema deveria validar o campo e impedir valores negativos, exibindo uma mensagem de erro.

* Severidade / Impacto:
Alta — valores inválidos podem comprometer o funcionamento da aplicação.

### Bug 3 — Sistema permite data de término anterior à data de início

* Descrição:
O sistema permite cadastrar um curso com data de término anterior à data de início, o que gera inconsistência lógica.

* Passos para reproduzir:

Acessar a tela de cadastro de curso

Preencher os campos do formulário

Inserir uma data de início posterior à data de término

Clicar em Cadastrar curso

* Resultado atual:
O sistema permite o cadastro do curso mesmo com datas inconsistentes.

* Resultado esperado:
O sistema deveria validar as datas e impedir o cadastro quando a data de término for anterior à data de início.

* Severidade / Impacto:
Média — pode gerar inconsistências nas informações dos cursos.

### Bug 4 — Script inserido no campo de texto é removido sem feedback ao usuário

* Descrição:
Ao inserir um script como <script>alert(1)</script> em campos de texto, o sistema remove o conteúdo sem apresentar feedback ao usuário.

* Passos para reproduzir:

Acessar a tela de cadastro de curso

Inserir <script>alert(1)</script> no campo Nome do curso

Clicar em Cadastrar curso

* Resultado atual:
O script não é exibido após o cadastro e aparentemente é removido automaticamente.

Resultado esperado:
O sistema deveria

Bloquear a inserção e informar o usuário, ou

Exibir o conteúdo como texto sanitizado.

* Severidade / Impacto:
Baixa — indica que existe algum tratamento de segurança, mas sem feedback ao usuário.
