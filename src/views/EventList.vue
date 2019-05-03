<template>
    <div>
        <h1>Event Listing</h1>
        <EventCard v-for="event in events" :key="event.id" :event="event"/> 
        <BaseIcon/>
    </div>
</template>

<script>
import EventCard from '@/components/EventCard.vue';
import axios from 'axios'
export default {
    components:{
        EventCard
    },

created() {
    axios.get('http://localhost:3000/events').then(response => {
        console.log(response.data)
        this.events = response.data
    })
    .catch(error =>{
        console.log('No jala carnal: ' + error.response)
    })
}
};  
</script>
