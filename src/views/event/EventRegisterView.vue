<script setup lang="ts">
import { ref } from 'vue'
import { type EventItem } from '@/type'
// import EventService from '@/services/EventService';
// const event = ref<EventItem | null> (null)
import type { PropType } from 'vue';
import {useRouter} from 'vue-router'
import {useMessageStore} from '@/stores/message';
const store = useMessageStore()



const props = defineProps ({
event: {
    type: Object as PropType<EventItem>,
        require: true
}
})
const router = useRouter()
function register() {
   // router.push({
     //   name: 'event-detail',
       // params: {
         //   id: props.event?.id
        //}
    //})
    store.updateMessage('You are successfully registered for ' +props.event?.title)
setTimeout(() => {
    store.resetMessage()
},3000)
router.push({
    name: 'event-detail',
    params: {
        id: props.event?.id
    }
})
}
// const props = defineProps({
//     id: String
// })
//defineProps({
  //  event: {
    //    type: Object as PropType<EventItem>,
      //      require: true
    //}
//})

//     EventService.getEventByID(Number(props.id)).then((response) => {
//         event.value = response.data
//     }).catch(error =>{
//         console.log(error)
//     })

</script>
    <template>
    <!-- <div v-if="event">
        <h1>{{ event.title }}</h1>
        <div id="nav">
            <router-link :to="{name: 'event-detail', params:{id}}">Details</router-link>
            <router-link :to="{name: 'event-register', params:{id}}">Register</router-link>
            <router-link :to="{name: 'event-edit', params:{id}}">Edit</router-link>
        </div> -->
        <p>Registration from here</p>
        <button @click="register">Register Me</button>
    <!-- </div> -->
</template>