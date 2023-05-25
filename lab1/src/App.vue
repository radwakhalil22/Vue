<template>
 <div>
  <FormComponent/>
 </div>
</template>

<script>
import FormComponent from './components/Form.vue'
export default (await import('vue')).defineComponent( {
  name: 'App',
  components: {
    FormComponent
  }
  , data(){
    return{}
  }
});
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
