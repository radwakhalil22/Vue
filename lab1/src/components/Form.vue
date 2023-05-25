<template >
    <button @click="show('form')">Form</button>
    <button @click="show('admin')">Admin</button>
    <button @click="show('user')">Users</button>
    <div>
        <div>
            <div  v-if="this.Btnvalue=='admin'">
                <AdminComponent :AdminFilter = "AdminFilter" @deleteAdmin="deleteAdmin"/>
            </div>
            <div v-else-if="this.Btnvalue=='user'">
                <UsersComponent :UserFilter = "UserFilter" @deleteUser="deleteUser" />
            </div>
            <div v-else class="login-box" >
                <!-- {{ JSON.stringify(userData) }} -->
                <!-- {{ arr }} -->
                <!-- {{ AdminFilter() }} -->
                <form  @submit.prevent = "FillArray">
                    <div class="user-box">
                    <input type="text" name="name" v-model="userData.name">
                    <label>name</label>
                    </div>
                    <div class="user-box">
                    <input type="text" name="age" v-model="userData.age">
                    <label>age</label>
                    </div>
                    <div class="d-flex">
                        <ul>
                            <li>
                                <input type="radio" name="role" id="user" value="user" @click="userData.role = $event.target.value">
                                <label for="user">User</label>
                            </li>
                            <li>
                                <input type="radio" name="role" id="admin" value="admin" @click="userData.role = $event.target.value">
                                <label for="admin">Admin</label>
                            </li>
                        </ul>
                    </div>
                    <button type="submit">
                        SEND
                    <span></span>
                    </button>
                </form>
    
            </div>
        </div>
    </div>
</template>
<script>
import AdminComponent from './Admin.vue'
import UsersComponent from './Users.vue'
export default(await import('vue')).defineComponent ({
    name:"FormComponent",
    components:{
        AdminComponent,
        UsersComponent,
    },
    data(){
        return{
            arr:[],
            userData: {
                name:'',
                age:'',
                role:'',
            },
            Btnvalue:'form'
        }
    }, 
    methods:{
        FillArray(){
            this.arr.push(this.userData);
            
            this.userData = {
                    name:'',
                    age:'',
                    role:'',
                }
        },
        deleteAdmin(index){
            this.AdminFilter.splice(index,1)
        },
        deleteUser(index){
            this.UserFilter.splice(index,1)
        },
        show(target){
            if(target =='admin'){
                this.Btnvalue = 'admin'
            }
            else if(target =='user'){
                this.Btnvalue = 'user'
            }
            else if(target =='form'){
                this.Btnvalue = 'form'
            }
        }
    },
    computed:{
            AdminFilter(){
                return this.arr.filter((d)=>d.role === 'admin')
            },
            UserFilter(){
                return this.arr.filter((d)=>d.role === 'user')
                },
    }
        
});
</script>
<style >
    .login-box {
        position: absolute;
        top: 50%;
        left: 50%;
        width: 400px;
        padding: 40px;
        transform: translate(-50%, -50%);
        background: rgba(24, 20, 20, 0.987);
        box-sizing: border-box;
        box-shadow: 0 15px 25px rgba(0,0,0,.6);
        border-radius: 10px;
        }

    .login-box .user-box {
        position: relative;
        }

    .login-box .user-box input {
        width: 100%;
        padding: 10px 0;
        font-size: 16px;
        color: #fff;
        margin-bottom: 30px;
        border: none;
        border-bottom: 1px solid #fff;
        outline: none;
        background: transparent;
        }

    .login-box .user-box label {
        position: absolute;
        top: 0;
        left: 0;
        padding: 10px 0;
        font-size: 16px;
        color: #fff;
        pointer-events: none;
        transition: .5s;
        }

    .login-box .user-box input:focus ~ label,
    .login-box .user-box input:valid ~ label {
        top: -20px;
        left: 0;
        color: #bdb8b8;
        font-size: 12px;
    }

    .login-box form button {
        position: relative;
        display: inline-block;
        padding: 10px 20px;
        color: #000;
        font-size: 16px;
        text-decoration: none;
        text-transform: uppercase;
        overflow: hidden;
        transition: .5s;
        margin-top: 40px;
        letter-spacing: 4px
    }

    .login-box button:hover {
        background: #03f40f;
        color: #fff;
        border-radius: 5px;
        box-shadow: 0 0 5px #03f40f,
                    0 0 25px #03f40f,
                    0 0 50px #03f40f,
                    0 0 100px #03f40f;
        }

        .login-box button span {
        position: absolute;
        display: block;
        }

        @keyframes btn-anim1 {
        0% {
            left: -100%;
        }

        50%,100% {
            left: 100%;
        }
        }

        .login-box button span:nth-child(1) {
        bottom: 2px;
        left: -100%;
        width: 100%;
        height: 2px;
        background: linear-gradient(90deg, transparent, #03f40f);
        animation: btn-anim1 2s linear infinite;
}
</style>