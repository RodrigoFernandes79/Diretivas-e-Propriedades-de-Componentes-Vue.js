<template>
<div id="app">
	<h1 v-if="mostrar">DIRETIVAS v-if</h1> <!--esconde visualmente e também no console.log quando false-->
	<h1 v-show="mostrar">DIRETIVAS v-show</h1> <!--esconde apenas visualmente-->
	<!--v-if também pode estar associado a v-else-if e v-else usados para rendeirizar através de condicionais-->
	<h1 v-if="state ==='loading'">loading</h1> <!--se v-if é igual a loading ,ele mostra loading-->
	<h1 v-else-if="state === 'error'">Error</h1><!--se nao for igual a loading, e se for igual a error, ele mostra error-->
	<h1 v-else-if="message.length === 0">No data Avaliable</h1>
	<h1 v-else>{{message}}</h1>
	<!--v-bind renderiza a propriedade passada no elemento da variável-->
	<a v-bind:href="url">Site</a> <!--usando ov-bind pra passar a propriedade url que tem como elemento o nome do site-->
	<!-- podemos apenas passar :href sem precisar escrever v-bind-->

	<!--v-bind renderiza css atraves do v-bind:style: Atenção pra colocar sempre entre colchetes e com camelCase-->
	<h1 style="font-size: 10px" v-bind:style="{color: 'red',fontSize:'60px'}">Diretiva v-bind</h1>
	<!--o style també pode ser chamado uma propriedade dentro de um array:-->
	<h1  v-bind:style="[color, fontSize]">Diretiva v-bind2</h1> <!--declarando em data()-->
</div>
</template>

<script>

export default {
name:'App',
components:{},
data() {
return{
mostrar:false,
state:'completed',
message:'hello:world',
url:'www.google.com',
color:{color:'red'},
fontSize:{fontSize:'60px'},
};
}
}
</script>

<style lang='scss'>
*{
	margin: 0;
	padding: 0;
}
#app {
display:flex;
align-items: center;
text-align: center;
justify-content: center;
height: 100vh;
flex-direction: column;
  color: #2c3e50;
}

</style>
