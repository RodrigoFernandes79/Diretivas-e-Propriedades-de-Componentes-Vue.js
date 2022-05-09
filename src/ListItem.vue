<template>
<div>
	<li>{{item}}</li>

<!--CUSTOMIZANDO O EVENTO DE CLICK: PARA PASSAR A FUNÇÃO INCREMENT3 NO CLICK, COLOCAMOS $EMIT
E O NOME DO EVENTO COLOCADO NO TEMPLATE DA CLASSE PAI. COMO SEGUNDO PARAMETRO, PASSAMOS A
CUSTOMIZAÇAO/ALTERAÇÃO DO EVENTO,QUE NO NOSSO CASO, QUEREMOS CONTAR DE 5 EM 5. O TERCEIRO
PARÂMETRO É O EVENTO EM SI, QUE AO CLICAR NO MOUSE ELE REALIZA O EVENTO-->
<button @click="$emit('customEvent', 5, $event)">Click me</button>
</div>
</template>
<script>
export default {
	name:'ListItem',
props:{
	item:Object,
}
}
</script>
