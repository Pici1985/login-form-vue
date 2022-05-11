<template>
    <div>
        <form>
            <label>Email:</label>
            <input type="email" required v-model="email">
            <br>
            <label>Password:</label>
            <input type="password" required v-model="password">

            <label>Role:</label>
            <br>
            <select v-model="role">
                <option value="Developer">Web Developer</option>
                <option value="Designer">Web Desginer</option>
            </select>
        </form>
        <p> Your email is: {{ email }} </p>
        <p> Password is: {{ password }}</p>
        <p> Your Job title is: {{ role }}</p>
    </div>
</template>

<script>
export default {
    data(){
        return{
            email: '',
            password: '',
            role: '',
        }
    }
}
</script>

<style>
    form {
        max-width: 420px;
        margin: 30px auto;
        background: white;
        text-align: left;
        padding: 40px;
        border-radius: 10px;
    }
    label {
        color: #aaa;
        display: inline-block;
        margin: 20px 0 15px;
        font-size: 0.6em;
        text-transform: uppercase;
        letter-spacing: 1px;
        font-weight: bold;
    }
    input, select {
        display: block;
        padding: 10px 6px;
        width: 100%;
        box-sizing: border-box;
        border: none;
        border-bottom: 1px solid #ddd;
        color: #555;
    }


</style>