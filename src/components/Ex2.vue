<script>
    export default { 
        data() {
            return {
                width: 'auto',
                height: 'auto',
                myImg: '/assets/me.png'
            }
        },
    }
</script>

<template>

    <!-- add code here -->
        <img v-bind:src="myImg" :width="width" :height="height"></img>
   
</template>
