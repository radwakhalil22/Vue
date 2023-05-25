<template lang="">
    <div >
        <div v-for="user,index in UserFilter" :key="user">
            <p>{{user.name}}</p>
            <p>{{user.age}}</p>
            <p>{{user.role}}</p>
            <p>{{index}}</p>
            <button class="text-danger" @click="$emit('deleteUser', index)">X</button>
        </div>
    </div>
</template>
<script>
export default (await import('vue')).defineComponent( {
    name: "UsersComponent",
    props:['UserFilter']
});
</script>
<style lang="">
    
</style>