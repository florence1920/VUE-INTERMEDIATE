<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="fas fa-plus addBtn"></i>
        </span>
    </div>
</template>

<script>
export default {
    data: function(){
        return {
            newTodoItem:""
        }
    },
    methods :{
        addTodo: function(){
            //저장하는 로직
            localStorage.setItem(this.newTodoItem,this.newTodoItem);
            this.clearInput();
        },
        clearInput:function(){
            this.newTodoItem='';
        }
    }
}
</script>

<style scoped>
input:focus {outline: none;}
.inputBox {background: #fff; height: 50px; line-height:50px; border-radius: 5px;}
.inputBox input {width: 92%; height: 40px; border-radius: 5px; border-width: 0; font-size:0.9rem; font-family: Ubuntu, sans-serif;}
.addContainer {float:right; display: block; width: 5%; border-radius: 0 5px 5px 0; cursor: pointer; background: linear-gradient(to right, #6478FB, #8763FB);}
.addBtn {color:#fff; vertical-align: middle;}

</style>