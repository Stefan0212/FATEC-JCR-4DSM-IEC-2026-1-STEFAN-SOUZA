# Codigo do workflow(ci.yml)/tarefa da aula 3:


# Nome do workflow (aparecerá na aba Actions)
name: CI Simples

# Eventos que disparam o workflow:
# - push (quando algo é commitado)
# - pull_request (quando há PR)
on:
  push:
    branches: [ dev2 ] # dispara apenas quando o commit é na branch dev
  pull_request:
    branches: [ dev2 ] # dispara quando há PR para dev

jobs:
  # Definindo um job chamado "build"
  build:
    runs-on: ubuntu-latest # ambiente que o GitHub usa (máquina Linux)

    steps:
      # 1. Baixar o código do repositório
      - name: Checkout do repositório
        uses: actions/checkout@v4

      # 2. Verificação de sintaxe e estrutura do projeto
      - name: Verificar arquivos do projeto
        run: |
          echo "=== Verificando estrutura de arquivos ==="
          ls -la
          echo "=== Verificando se arquivos essenciais existem ==="
          test -f README.md && echo "README.md encontrado" || echo "README.md não encontrado"

      # 3. Verificar se há arquivos YAML válidos
      - name: Verificar arquivos YAML
        run: |
          echo "=== Listando arquivos YAML no projeto ==="
          find . -name "*.yml" -o -name "*.yaml" | grep -v ".git"

      # 4. Teste de funcionamento final
      - name: Teste de Funcionamento
        run: echo "Pipeline do projeto INPE executado com sucesso!"
