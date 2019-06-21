<template>
    <ul>
        <li>walk the dog</li>
        <li>clean the room</li>
        <li>do your assignment</li>
        <li v-for= "(todo, index) in todos"
        :key="index"
        @click= "todoDone(index)">
         {{index}} - {{ todo }}</li>
    </ul>
</template>
<script>
export default {
    props:{
        todos:{
            type: Array,
            required: true,
        }
    },
    methods:{
        todoDone(index){
            console.log(index);
            // $emit emits an event from the child component to the parent component
            this.$emit("removetodo", index);
        }
    }
}
</script>