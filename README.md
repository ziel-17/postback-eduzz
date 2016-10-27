### Sobre o postback
O recurso de postback permite que você receba notificações de alguns eventos que ocorrem dentro do sistema, possibilitando que alem do produtor, o afiliado tambem tenha um melhor controle sobre seu negócio.

No momento estão disponíveis apenas as ações referentes ao `rastreamento` de campanhas:
* TRACKER.CHECKOUT - Acionado ao carregamento de um carrinho
* TRACKER.THANKYOU - Acionado quando o cliente chega até a página de obrigado  
* TRACKER.BOLETO   - Acionado sempre que um boleto é visualizado

As informações de alteração de status de compra estão disponíveis apenas para os produtores através do webhook. Muito em breve essas notificações estarão unificadas via postback tambem para os afiliados

***

### Cadastro de URL
1. Logue em  sua conta e acesse o menu `Afiliado >> Meus Funis / Campanhas`
2. Na listagem de suas campanhas, clique no ícone conforme indicado na imagem abaixo: ![alt tag](https://raw.githubusercontent.com/deveduzz/postback-eduzz/master/postback1.jpg)
3. Na tela seguinte, cadastre a URL onde você deseja receber as notificações do sistema   ![alt tag](https://raw.githubusercontent.com/deveduzz/postback-eduzz/master/postback2.jpg)
***

### Requisições válidas e retentativas
No caso de falha, são realizados 5 tentativas no intervalo de 12 horas ( 2m,6m,24m,2h,12h), após esse periodo sem sucesso, a postback é cancelado.
Consideramos válidas todas as requisicoes que retornam o status HTTP 200.
***

### Validação
Enviamos via `header` o parametro `X-EduzzApi` , que deve ser comparada com a Chave de API do Afiliado/Produtor que receberá o postback.

***
### Parametros enviados
