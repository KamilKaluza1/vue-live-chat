<template>
    <div class="container">
        <Navbar/>
        <ChatWindow/>
        <NewChatForm/>
    </div>
</template>

<script>

import getUser from '@/composables/getUser';
import {watch} from 'vue'
import { useRouter } from 'vue-router';
import Navbar from '../components/Navbar.vue'
import NewChatForm from '../components/NewChatForm.vue'
import ChatWindow from '../components/ChatWindow.vue'
export default{
    components: {Navbar, NewChatForm, ChatWindow},


    setup(){
        const router = useRouter()
        const {user} = getUser()

        watch(user, () =>{
            if(!user.value){
                router.push({name:'welcome'})
            }
        })

    }
    
}


</script>