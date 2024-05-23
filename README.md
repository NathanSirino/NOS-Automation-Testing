# NOS Automation Testing

Este repositório contém o projeto de testes automatizados utilizando o Postman para validar as APIs do sistema NOS. Ele inclui coleções e scripts que realizam diversas verificações, como a validação do esquema JSON, verificação do status da resposta e testes de conteúdo.

## Procedimento de Setup e Execução do Projeto

### Setup do Ambiente Postman

1. **Instale o Postman:**
   - Faça o download e a instalação do Postman a partir do [site oficial](https://www.postman.com/downloads/).

2. **Importe a Coleção:**
   - Importe a coleção fornecida (`NOS Automation Testing.postman_collection.json`) no Postman.
   - Para importar, abra o Postman e navegue até `File` > `Import` e selecione o arquivo JSON da coleção.

3. **Configure as Variáveis de Ambiente:**
   - No Postman, configure as variáveis de ambiente necessárias, como `baseUrl` e `token`.
   - As variáveis podem ser configuradas acessando a opção `Manage Environments` e adicionando os valores no ambiente correspondente.
   - Por exemplo, configure a variável `baseUrl` com o valor `https://gorest.co.in/`.

### Execução dos Testes

1. **Selecione a Coleção:**
   - No Postman, selecione a coleção importada (`NOS Automation Testing`).

2. **Execute os Testes:**
   - Clique em `Run` para executar todos os testes da coleção.
   - A execução pode ser feita individualmente em cada requisição ou em lote utilizando o `Collection Runner`.

3. **Verifique os Resultados:**
   - Após a execução, verifique os resultados dos testes na aba de execução.
   - Os resultados mostrarão se os testes passaram ou falharam, juntamente com detalhes das validações realizadas.

### Estrutura dos Testes

A coleção inclui os seguintes tipos de testes:

1. **Validação do Esquema JSON:**
   - Valida se a resposta da API corresponde ao esquema JSON esperado.

2. **Verificação do Status da Resposta:**
   - Verifica se o código de status HTTP das respostas é conforme esperado (e.g., 200, 201, 204).

3. **Verificação de Conteúdo:**
   - Verifica se os valores específicos na resposta da API atendem aos critérios definidos, como tipos de dados e valores específicos.

### Exemplo de Configuração de Variáveis no Postman

```json
{
  "baseUrl": "https://gorest.co.in/",
  "token": "seu_token_aqui"
}
```

### Exemplo de Execução de um Teste

- **Teste de Validação do Esquema JSON:**

```javascript
pm.test("Schema is valid for all items", () => {
    let allValid = true;
    for (let i = 0; i < response.length; i++) {
        const valid = validate(response[i]);
        if (!valid) {
            console.log(`Validation errors in item ${i}:`, validate.errors);
            allValid = false;
        }
    }
    pm.expect(allValid).to.be.true; 
});
```

- **Teste de Verificação de Status:**

```javascript
pm.test("Status code is 201", function() {
    pm.response.to.have.status(201);
});
```

## Conclusão

Com os passos acima, você estará pronto para configurar e executar os testes automatizados utilizando o Postman para o projeto NOS Automation Testing. Certifique-se de atualizar as variáveis de ambiente conforme necessário e verificar os resultados detalhadamente após cada execução de teste.

---
