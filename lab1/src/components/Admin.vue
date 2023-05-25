<template lang="">
    <div >
        <div v-for="admin,index in AdminFilter" :key="admin">
            <p>{{admin.name}}</p>
            <p>{{admin.age}}</p>
            <p>{{admin.role}}</p>
            <p>{{index}}</p>
            <button class="text-danger" @click="$emit('deleteAdmin', index)">X</button>
        </div>
    </div>
</template>
<script>


export default (await import('vue')).defineComponent( {
    name:"AdminComponent",
    props:[ 'AdminFilter'],
    methods:{

    },
    // emits:['deletingAdmin']
});

</script>
<style lang="">
    
</style>