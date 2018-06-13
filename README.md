
# Widget cartão de crédito - Faturamento

<p align="center">
  <img src="https://mag-widgethmg.mongeralaegonapi.p.azurewebsites.net/images/catalogo-cartaodecredito.png">
</p>

## Consumo via iframe

Esse passo não existe autenticação e basta apenas escolher um iframe e colá-lo em seu site.

<details><summary>Produção</summary>
<p>

```html
<iframe src="https://widget.mgaapi.p.azurewebsites.net/widget-cartao-credito/v1/"></iframe>
```

</p>
</details>

<details><summary>Homologação</summary>
<p>

```html
<iframe src="https://mag-widgethmg.mongeralaegonapi.p.azurewebsites.net/widget-cartao-credito/v1/"></iframe>
```

</p>
</details>

## Consumo via mgwidgets.js

> mgwidgets.js é a biblioteca da mongeral aegon para configurar `dinamicamente` widgets em sites parceiros

Você precisa fazer download da bilioteca ou utilizar a partir do nosso CDN:

```
https://cdn.mongeralaegon.com.br/libs/js/mgwidgets.js
```

Após isso você precisa inserir o a biblioteca antes do fechamento da tag ```body``` e começar a configurar o widget

```html
<script src="https://cdn.mongeralaegon.com.br/libs/js/mgwidgets.js" async></script>
```
``` javascript
const widgetsCartao = new mongeral.Widgets();
widgetsCartao.init({
  mode: 'development',
  widgets: [
    {
      clientId: 'custom',
      scope: 'faturamento cartaocredito',
      token: 'ajhsdklajsh-sdase123esq',
    },
  ],
});
```

E onde você quiser que o widget apareça você precisa criar um elemento html com os seguintes atributos

Atributos | Detalhes
----------|---------
mg-widget | Espera pelo nome do widget, esses nomes são pré-definidos
mg-version | A versão do widget 
mg-client-id | O ClientID 

```html
<div mg-widget="cartao-credito" mg-version="1" mg-client-id="Faturamento"></div>
```


## Parâmetros por querystring

Parâmetro | Obrigatório | Descrição
----------| ------------|----------
cnpj | Sim, se não houver CPF | Indica o CNPJ da empresa do convênio em que o pagador possui sua cobrança (ex. Mongeral Aegon)
cpf | Sim, se não houver CNPJ | Identifica o Pagador da cobrança
acao | Sim | Esse widget possui hoje duas ações disponíveis: DadosCobranca - Quando o pagador já possui cobrança de cartão de crédito, e deseja alterar os dados do cartão (cadastrar um novo cartão); e AlterarFormaCobranca - Quando o pagador possui cobrança de outra forma (boleto, débito) e quer alterar para cartão de crédito
IdentificadoresExternos | Sim | lista de identificadores de cobrança, de acordo com o sistema externo que comandou o faturamento. No caso das cobranças Mongeral Aegon, representam as inscrições do pagador
DataProximaCompetenciaAlteracao | Opcional | Formato AAAA-MM-dd -  Quando a alteração for agendada, preencha esse parâmetro para indicar em qual mês ela deve ser efetivada. O dia da alteração seguirá o dia de vencimento do pagador. Caso esse parâmetro não seja preenchido, ou venha preenchido com data anterior à atual, a alteração ocorrerá imediatamente (respeitando o dia do vencimento do pagador).

Um exemplo de como ficaria o widget com paramêtros

```html
<iframe src="https://widget.mgaapi.p.azurewebsites.net/widget-cartao-credito/v1/?cnpj=33608308000173&acao=DadosCobranca&IdentificadoresExternos=1059407541780&DataProximaCompetenciaAlteracao=2018-12-31"></iframe>
```

## Temas disponíveis

> Os temas são formas visuais diferentes para a mesma experiência

Esse widget não possuí temas.

## Keywords assinadas e publicadas

Keywords |
--------
cpf | 
cnpj |
cpfPagador |

## Documentação do Widget

[Documentação do widget de cartão de crédito](#)
