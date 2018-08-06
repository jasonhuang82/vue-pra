<script>
  import TodoInput from '../TodoInput';
  import TodoItem from '../TodoItem';
  export default {
    data(){
      return{
        sortState: 'asc',
        todos: [
          {
            id: 1,
            title: 'test'
          }
        ]
      }
    },
    components:{
      TodoInput,
      TodoItem
    },
    methods:{
      addTodo(title){
        this.todos.push({
          id: +new Date(),
          title
        });
        
      },
      delTodo(id){
        // this.todos.splice(idx,1);
        this.todos = this.todos.filter(todo => todo.id !== id);
      },
      sortItem(){

          switch (this.sortState) {
            case 'asc':
              this.sortState = 'desc'
              return a.id - b.id;
              break;
            case 'desc':
              this.sortState = 'asc'
              return b.id - a.id;
              break;
            default:
              return null;
              break;
          }
        
        
      }
    }
  }
</script>

<template src="./template.html"/>
<style scoped lang="scss" src="./style.scss"  />