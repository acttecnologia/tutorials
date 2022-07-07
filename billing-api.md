# API Bilhetagem

Esta é uma API para clientes de PABX IP da Act Tecnologia. Ela retorna histórico e dados das ligações efetuadas na nossa central.


## Obter ligações [GET]

Para obter o histórico de ligações, basta enviar uma requisição do tipo GET para a seguinte URL:


```url
https://gerenciador.acttecnologia.com.br/api/billing.php?api_token=<API_TOKEN>&start_date=<INITIAL_DATE>&end_date=<FINAL_DATE>&disposition=<DISPOSITION>&type=<TYPE>
```

### Onde:
- ```<API_TOKEN>``` deve ser o token que você recebeu para autenticação nessa API.


- ```<INITIAL_DATE>``` corresponde a data inicial do período desejado e deve ter o formato ```yyyy-mm-dd```


- ```<FINAL_DATE>``` corresponde a data final do período desejado e deve também, ter o formato ```yyyy-mm-dd```


- ```<DISPOSITION>``` pode ser:

    ```answered```: Ligações atendidas;

    ```no_answer```: Ligações não atendidas;


- ```<TYPE>``` pode ser:

    ```incoming```: Ligações de entrada;

    ```outgoing```: Ligações de saída;

    ```all```: Ambas as anteriores.

#### Observações:
- O período máximo para trazer ligações simultaneamente será de 3 meses. Caso seja definido um período maior na requisição, será retornado erro 400 Bad Request.
- Caso apenas data inicial ou apenas data final sejam definidas, ou o formato da data seja inválido, também será retornado erro 400 Bad Request.

#### Veja um exemplo de URL:

```url
https://gerenciador.acttecnologia.com.br/api/billing.php?api_token=5468asd48asd4a6s8da98d4a68dads58&start_date=2022-06-01&end_date=2022-06-28&disposition=answered&type=outgoing
```
