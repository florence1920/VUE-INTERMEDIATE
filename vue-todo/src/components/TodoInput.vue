<template>
    <div class="inputBox shadow">
        <input type="text" v-model="newTodoItem" v-on:keyup.enter="addTodo">
        <span class="addContainer" v-on:click="addTodo">
            <i class="fas fa-plus addBtn"></i>
        </span>
        <Modal v-if="showModal" @close="showModal = false">
            <h3 slot="header">
                경고!
                <i class="fas fa-times closeModalBtn" v-on:click="showModal = false"></i>
            </h3>
            <h3 slot="body">내용을 입력해주세요</h3>
        </Modal>
    </div>
</template>

<script>
import Modal from '@/components/common/Modal.vue'
export default {
    data: function(){
        return {
            newTodoItem:"",
            showModal:false
        }
    },
    methods :{
        addTodo: function(){
            if(this.newTodoItem !== ''){
                this.$emit('addTodoItem',this.newTodoItem);
                this.clearInput();
            }else{
                this.showModal = !this.showModal;
            }
        },
        clearInput:function(){
            this.newTodoItem='';
        }
    },
    components:{
        Modal
    }
}
</script>

<style scoped>
input:focus {outline: none;}
.inputBox {background: #fff; height: 50px; line-height:50px; border-radius: 5px;}
.inputBox input {width: 92%; height: 40px; border-radius: 5px; border-width: 0; font-size:0.9rem; font-family: Ubuntu, sans-serif;}
.addContainer {float:right; display: block; width: 5%; border-radius: 0 5px 5px 0; cursor: pointer; background: linear-gradient(to right, #6478FB, #8763FB);}
.addBtn {color:#fff; vertical-align: middle;}
.closeModalBtn{color:#42b983;}
</style>