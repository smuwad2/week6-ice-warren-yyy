<script>
    export default { 

       // add code here
       data() {
        return {
            loginField: "username"
        }
    }
}
</script>

<template>
    <h1>Please select your login option</h1>
    <!-- Add/modify code in the following to have a dropdown list 
        which lets the user to select either to login with username or email -->

    <select v-model="loginField">
        <option value="username" selected>Username login</option>
        <option value="email">Email login</option>
    </select>
    
    <div v-if="loginField == 'username'">
        <label>Username</label>
        <input placeholder="Enter your Username">
    </div>
    <div v-else>
        <label>Email</label>
        <input placeholder="Enter your Email">
    </div>
</template>