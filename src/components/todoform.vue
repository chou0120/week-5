<template>
<div>
    <slot name="title"></slot>
     <form @submit.prevent="addtodo" >
           <input type="text" v-model="newtodo">
           <input type="submit" name="Add">
           <slot name="desc"></slot>
           <slot>Default slot, placeholder content</slot>
       </form>
</div>
</template>
<script>
export default {
    data(){
        return{
            newtodo: ""
        };
       
    },
     methods: {
           addtodo(){
               if(this.newtodo.length){
this.$emit('newtodo', this.newtodo);
this.newtodo = "";
               }
           } 
        },
}
</script>
<style scoped>
input{
    min-width: 200px;
    padding: 20px 10px;
    margin: 0 auto;
    font-size: 1.5rem;
}
</style>


