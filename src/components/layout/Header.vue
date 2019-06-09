<template>
    <header class="header">
        <h2 style="font-weight: bold;">TODO App</h2>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>
    .header {
        background: #36daf7; 
        color: #ffffff;
        padding: 10px;
        text-align: center;
        font-weight: bold;
    }

    a {
        color: #ffffff;
        text-decoration: none;
    }
</style>
