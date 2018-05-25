<template>
  <div id="app">
    <h1>{{title}}</h1>
    <input type="text" class="input" v-model="newItem" v-on:keyup.enter="addNew">
    <div class="todo">
    	<h3 class="db">待办事项</h3>
      <ul class="list">
        <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinish(item)">
        {{item.label}}
        </li>
      </ul>
    </div>
  </div>
</template>


<script>

export default {
   data:function() {
    return {
      title: 'my daily todolist',
      items:[
          {
            label:'HTML+CSS',
            isFinished:false
  
          },
          {
            label:'javascript',
            isFinished:false
  
          }
      ],
      newItem:''
    }
  },
  methods:{
    toggleFinish:function(item){
      item.isFinished=!item.isFinished;
    },
    addNew:function(){
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem='';
    }
  
  }
}
</script>

<style>
body{
	margin-top: -25px;
}
	#app{
		width: 320px;
		height: 480px;
		margin: auto;
		background: url(assets/th.jpg);

	}
	h1{
		padding-top: 30px;
		color: hotpink;
	}
	.todo,.notdo{
		width: 320px;
		display: flex;
		justify-content: space-around;
	}
	.db{
		color: brown;
		padding-top: 10px;
	}
	.input{
		width: 200px;
		height: 30px;
		border-radius: 5%;
		border-color: palevioletred;
	}
	ul{
		list-style: none;
		font-size: 20px;
		padding-top: 10px;
		color: royalblue;
	}
.finished{
  display: none;
}
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
.clear{
	margin-top: 30px;
	width: 55px;
	height: 30px;
	background: palevioletred;
	border-color: burlywood;
	font-weight: bold;
	font-size: 15px;
}
</style>