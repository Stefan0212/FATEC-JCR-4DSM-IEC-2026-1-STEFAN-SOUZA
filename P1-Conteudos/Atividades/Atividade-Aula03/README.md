# Codigo do workflow(ci.yml)/tarefa da aula 3:

      - name: Verificar arquivos do projeto
        run: |
          echo "=== Verificando estrutura de arquivos ==="
          ls -la
          echo "=== Verificando se arquivos essenciais existem ==="
          test -f README.md && echo "README.md encontrado" || echo "README.md não encontrado"

      3. Verificar se há arquivos YAML válidos
      - name: Verificar arquivos YAML
        run: |
          echo "=== Listando arquivos YAML no projeto ==="
          find . -name "*.yml" -o -name "*.yaml" | grep -v ".git"

      4. Teste de funcionamento final
      - name: Teste de Funcionamento
        run: echo "ipeline do projeto INPE executado com sucesso!"


<img width="1017" height="433" alt="image" src="https://github.com/user-attachments/assets/a9839191-db40-4e7b-9553-6f15d337b93b" />
