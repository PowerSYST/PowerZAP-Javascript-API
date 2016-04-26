##Introdução
Esta biblioteca lhe permite criar páginas personalizadas utilizando as ferramentas do PowerZAP.

##Exemplo de uso
(Repositório do Exemplo)[https://github.com/PowerSYST/PowerZAP-Javascript-Example]

##Instalação
```
<script src="https://widget.powerzap.com.br/js/api.min.js charset="utf-8"></script>
```

##Métodos
__Iniciar objeto__
```
chat = new PowerZAP_API({
    hash    : "HASH_EMPRESA", //Diponível em seu painel
    company : ID_EMPRESA //Diponível em seu painel
}, function(powerzap) {

    //Chama os métodos abaixo

});
```

__Iniciar um atendimento com o cliente__

```
var object = {
	name :  'Nome completo do cliente', //João Lima
	whatsapp: 'Número do Whatsapp com DDI e DDD', //+55 (99) 9 9999-9999
	message : 'Texto da mensagem a ser enviada', //Olá tudo bem? 
	department: 'id do departamento' // 10
};

powerzap.initChat(object, function(response) {
    //Callback com sucesso

}, function(response) {
    //Callback caso ocorra um erro

});
```

__Requisitar o Me Chama no WhatsApp__

```
var object = {
	name :  'Nome completo do cliente', //João Lima
	whatsapp: 'Número do Whatsapp com DDI e DDD', // +55 (99) 9 9999-9999
	department: 'id do departamento' // 10
};

powerzap.requestCallWhatsApp(object, function(response) {
  //Callback com sucesso

}, function(response) {
  //Callback caso ocorra um erro

});
```

__Finalizar o chat aberto__

```
var object = {};

powerzap.closeChat(object, function(response) {
  //Callback com sucesso

}, function(response) {
  //Callback caso ocorra um erro

});
```

__Enviar o Feedback do atendimento finalizado__

```
var object = {
    score: 'Nota do atendimento de 0-5', // 5
    message: 'Comentário sobre o atendimento' //Gostei muito do atendimento
};

powerzap.sendFeeback(object, function(response) {
    //Callback com sucesso

}, function(response) {
    //Callback caso ocorra um erro

});
```

__Recebe notificações sempre que houver uma alteração no estado da conversa ou uma nova mensagem__
```
powerzap.notificationListener(function(res) {

    for(var i in res.messages) {
        //Messages

    }

    for(i in res.reads) {
      //List ids messages reads

    }

    if (res.closed) {
        //Chat finalizado

    } else {
        //Chat aberto

    }
});
```