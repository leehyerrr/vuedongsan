<template>
<div class="sect">
    <img :src="a.image">
    <!-- <h4 @click="modal(a.id)">{{a.title}}</h4> -->
    <h4 @click="send">{{a.title}}</h4>
    <!-- <h4>{{a.title}}</h4> -->
    <!-- <p>{{i}}</p> -->
    <p>{{a.price}}</p>
</div>
</template>

<script>
export default {
    name:"Card",
    props:{
        a:Object,
        // modal:Function,
    },
    methods: {
        send(){
            this.$emit('openModal2',this.a.id)
            
        },

    }
}
</script>

<style>

</style>