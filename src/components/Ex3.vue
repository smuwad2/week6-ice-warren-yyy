<script>
        // <div id='app'></div>
        const app = Vue.createApp({
            data() {
                return {
                    // key: value
                    loginType: 'username', // 'username' or 'email'
                };
            }, // data
            // computed: { 
            //     derivedProperty() {
            //         return false;
            //     }  
            // }, // computed
            // created() { 
            // },
            // mounted() { 
            // },
            methods: {
                methodName() {

                }
            } // methods
        });
        const vm = app.mount('#app'); 
</script>

<template>
    <h1>Please select your login option</h1>
    <!-- Add/modify code in the following to have a dropdown list 
        which lets the user to select either to login with username or email -->
    <select v-model="loginType">
        <option selected value="username">Username login</option>
        <option>Email login</option>
    </select>
    
    <div v-if="loginType === 'username'">
        <label>Username</label>
        <input placeholder="Enter your username">
    </div>
    <div v-else>
        <label>Email</label>
        <input placeholder="Enter your email address">
    </div>
</template>

