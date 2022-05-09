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

	<!--Trabalhando com PROPS=> são passagens de dados passando valor de pai para filho-->
	<Title titulo="Título1" /> <!--para serem renderizados na classe pai(App.vue), usamos a
	propriedade props export default da classe filho(Title.vue)-->
	<!--por default, o props passa uma string , e se quisermos passar um objeto, array, number..etc,
	temos que colocar o v-bind na propriedade do HTML-->
	<Title v-bind:titulo="2" />

	<Title subtitulo="subtitulo" />

	<!--diretiva v-for-->
	<ul>
		<li v-for="(item,index) of todos" :key="index" >{{ item }}</li>

	</ul>
	<!--endendendo como funciona o v-for em array de objetos: o primeiro parametro é o valor,
	o segundo é a chave e o terceiro é o index(a posição do array)-->
	<ul>
		<li v-for="(valor,chave,index) of todos" :key="index">
			{{chave}} : {{valor}} => {{index}}
			</li>
	</ul>
	<!--renderizando o listItem.vue-->
	<ul>
		<ListItem v-for="(item,index) in lista" :key="index" :item="item" />
	</ul>

	<!--TRABALHANDO COM V-ON:	são DIRETIVAS DE MODIFICADORES DE ACESSO COMO O @click , 	NA VERDADE
	O V-ON PODE SER SUBSTITUIDO PELO CARACTERE @-->
	<button @click="count1++">Click1 {{count1}}</button>
	<button @click="increment">Click2 {{count2}}</button>
	<button @click="increment2(2)">Click3 {{count3}}</button>
<!-- DIRETIVA V-ON COM $EVENT. O $EVENT AO SER ACIONADO, ELE REALIZA UM EVENTO QUE FOI DETERMINADO
PARA ELE-->
<input type="text" @input="say('hello',$event)"> <!--QUANDO FOR INSERIDO UM TEXTO NO INPUT, ELE
VAI REALIZAR UM EVENTO(MOSTRARÁ UMA MENSAGEM DE HELLO-->


<!--EVENTO CUSTOMIZADO: PASSANDO O EVENTO DA CLASSE FILHO(LISTITEM.VUE) PARA SEREM RENDERIZADOS
NA CLASSE PAI(APP.VUE)-->
<ListItem @customEvent="increment3" />{{ count1 }}
</div>
</template>

<script>
import Title from './Title.vue';
import ListItem from './ListItem.vue';
export default {
name:'App',
components:{
	//Title,
	ListItem,
},
data() {
return{
	//diretivas v-if e vshow:
mostrar:false,
//diretivas v-else-if e v-else:
state:'completed',
message:'hello:world',
//diretiva v-bind:
url:'www.google.com',
color:{color:'red'},
fontSize:{fontSize:'60px'},
//diretiva v-for:
todos: {
	item1:'Item 1',
	item2:'Item 2',
	item3:'Item 3',
},
lista:[
	{label:'item',value:1},
	{label:'hello',value:'world'},
	{label:'Harry',value:'Potter'},
],
//DIRETIVA V-ON NO BUTTON:
count1:0,
count2:0,
count3:0,
};
},
//CRIANDO OS MÉTODOS DA DIRETIVA V-ON NO BUTTON:
methods:{
increment(){
	this.count2++;
},
increment2(quantidade){
	this.count3+=quantidade;
},
//CRIANDO O MÉTODO DO INPUT COM $EVENT:
say(word,event){
	alert(word,event);
},
//CRIANDO O MÉTODO INCREMENT3 PARA EVENTO CUSTOMIZADO(CLASSE FILHO->PAI)
increment3(parametro2, parametro3){ // passando o parametro2 da classe filho para customizar o evento
this.count1+=parametro2;
alert('hello',parametro3)//passando o parametro 3 como evento ao clicar no mouse ele mostra a
//mensagem 'hello'
},
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
