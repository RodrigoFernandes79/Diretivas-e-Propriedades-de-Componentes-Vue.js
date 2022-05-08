<template>

	<!--no v-bind="$attrs",todos os atributos HTML da classe pai(ex: <div></div>),sairao
da classe pai e passarao para onde colocamos o v-bind(no caso no h1). com exceções de
class e style-->
	<h1 >{{titulo}}</h1>

</template>

<script>

export default {
	name:'Title',
	//renderizando a classe pai(App.vue) através do props:
props:{
	titulo:{
	type:String,  // podemos definir regras nas props como o tipo , se é obrigatório ou um valor default
	required:true,
	inheritAttrs:false, /*define se os atributos das classes HTML será usados ou não. com exceção
	do CLASS ou STYLE , que permanecerão e sempre estarão na tag pai do HTML*/
	},
	subtitulo:{
	type:String,
	required:false,
	default:'Default'
	}
},
data() {
return{

};
}
}
</script>
