<script>
    export default { 
        data() {
            return {
                // Add code here
                isActive: true,
                id: "demo1",
            }
        },
        methods: { 
   			// Add code here
            changeActive() {
                this.isActive = !this.isActive;
            }
		}
    }
</script>

<template>
    
    <!-- Modify code here -->
    <div class="container">
        <div v-bind:id="id" :class="{redBox: !isActive, blueBox: isActive}" class="m-2">
            div ID : {{id}} 
        </div>
        
        <button type="button" v-bind:onclick="changeActive" v-bind:class="{'btn btn-danger': !isActive, 'btn btn-primary': isActive}">Change Color</button>
    </div>

</template>

<style scoped>
    .redBox {
        background-color: red;
    }
    .blueBox {
        background-color: blue;
    }
    #demo1 {
        color: white;
    }
</style>
