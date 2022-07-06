# API Bilhetagem

Esta é uma API para clientes de PABX IP da Act Tecnologia. Ela retorna histórico e dados de suas ligações.


## Como utilizar

Para obter o histórico de ligações, basta enviar uma URL como a seguinte:

```
https://gerenciador.acttecnologia.com.br/api/billing.php?disposition=<DISPOSITION>&type=<TYPE>
```

### Onde:

- ```<DISPOSITION>``` pode ser:

    ```answered```: Ligações atendidas;

    ```noAnswer```: Ligações não atendidas;

    ```all```: Ambas as anteriores.



- ```<TYPE>``` pode ser:

    ```incoming```: Ligações de entrada;

    ```outgoing```: Ligações de saída;

    ```all```: Ambas as anteriores.

### Parâmetros opcionais:
Você também pode definir um período específico para que a API retorne os dados. Para isso usam-se os seguintes parâmetros:

- ```initialDate```: Data inicial do período desejado;

- ```finalDate```: Data final do período.

- ```Padrão (vazio)```: Caso nenhum período seja definido, serão trazidas apenas as ligações do dia atual da requisição;

- O formato da data deverá ser o seguinte: yyyy-mm-dd.

#### Observações:
- O período máximo para trazer ligações simultaneamente será de 3 meses. Caso seja definido um período maior na requisição, a API muda automaticamente para 3 meses.
- Caso apenas data inicial ou apenas data final sejam definidas, ou o formato da data seja inválido, o retorno será o padrão.

Veja um exemplo de URL com data definida:

```
https://gerenciador.acttecnologia.com.br/api/billing.php?initialDate=2022-06-01&finalDate=2022-06-28&disposition=answered&type=outgoing
```