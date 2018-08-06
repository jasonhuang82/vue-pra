<script>
  export default {
    data(){
      return{
        todoText: ''
      }
    },
    methods: {
      addItem(){
        this.$emit('addTodo',this.todoText);
        this.todoText = '';
      }
    }
  }
</script>

<template src="./template.html"/>
<style scoped lang="scss" src="./style.scss"  />