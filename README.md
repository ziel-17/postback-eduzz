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


| Parâmetro | Descrição |
| --- | --- |
| `event.action` | Ação de evento ( `TRACKER.CHECKOUT, TRACKER.BOLETO, TRACKER.THANKYOU` )
| `event.datetime` | Data e hora do evento no formato YYYY-MM-DD HH:MM:SS ex: 2016-10-26 22:02:25
| `invoice.id` | ID da fatura se houver.
| `invoice.value` | Valor da fatura se houver
| `invoice.status` | Status da fatura ( Ver tabela de status de pagamento )
| `invoice.paymentmethod` | Forma de pagamento ( Ver tabela de forma de pagamento )
| `invoice.datetime` | Data de criação da fatura ( Clicou em pagar ) no formato YYYY-MM-DD HH:MM:SS ex: 2016-10-26 22:02:25
| `invoice.paymentdate` | Data de pagamento se houver no formato YYYY-MM-DD HH:MM:SS ex: 2016-10-26
| `product.id` | Código do conteudo
| `product.name` | Nome do conteudo
| `customer.id` | ID do cliente se houver
| `customer.name` | Nome do cliente se houver
| `customer.email` | Email do cliente se houver
| `partner.id` | ID do afiliado se houver
| `partner.name` | Nome do afiliado se houver
| `partner.email` | E-mail do afiliado se houver
| `tracker.funnelkey` | Código da campanha se houver
| `tracker.utm_source` | Referencia informada na momento do clique (Ex: http://edz.la/XXXX?a=815959&utm_source=BANNER01)
| `tracker.utm_content` | Referencia informada no momento do clique (Ex: http://edz.la/XXXX?a=815959&utm_content=BANNER02)
| `tracker.utm_campaign` | Referencia informada no momento do clique (Ex: http://edz.la/XXXX?a=815959&utm_campaign=BANNER03)
| `tracker.utm_medium` | Referencia informada no momento do clique (Ex: http://edz.la/XXXX?a=815959&utm_medium=BANNER01)
| `tracker.ip` | IP de origem da transação
| `cart.key` | Código da pagina de checkout
| `cart.datetime` | Data de primeira abertura do checkout no formato YYYY-MM-DD HH:MM:SS ex: 2016-10-26 22:02:25

### Support or Contact
Having trouble with Pages? Check out our [documentation](https://help.github.com/pages) or [contact support](https://github.com/contact) and we’ll help you sort it out.
