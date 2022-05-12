<template>
    <div>
        <!-- submit.prevent is equal to e.preventDefault() -->
        <form @submit.prevent="handleSubmit">
            <label>Email:</label>
            <input type="email" required v-model="email">
            <br>
            <label>Password:</label>
            <input type="password" required v-model="password">
            <div v-if="passwordError" class="error">{{ passwordError }}</div>

            <label>Role:</label>
            <br>
            <select v-model="role">
                <option value="Developer">Web Developer</option>
                <option value="Designer">Web Desginer</option>
            </select>

            <div class="terms">
                <input type="checkbox" required v-model="terms">
                <label>Accept terms and conditions.</label>
            </div>

            <div>
                <input type="checkbox" value="Bazsi" v-model="names">
                <label> Bazsi </label>
            </div>
            <div>
                <input type="checkbox" value="Ivi" v-model="names">
                <label> Ivi </label>
            </div>
            <div>
                <input type="checkbox" value="Sophie" v-model="names">
                <label> Sophie </label>
            </div>

            <label>Skills:</label>

            <!-- <input type="text" required v-model="tempSkill" @keyup="addSkill">  -->
            <input type="text" v-model="tempSkill" @keyup.alt="addSkill"> 
            <!-- @keyup.alt asks for the alt button to be pressed, also the character won`t show. KeyPress event still happens though. -->
            <div v-for="skill in skills" :key="skill" class="pill">
               <span @click="deleteSkill(skill)"> {{ skill }} </span>
            </div>

            <div class="submit">
                <button>Create Account</button>
            </div>

        </form>

        <p> Your email is: {{ email }} </p>
        <p> Password is: {{ password }}</p>
        <p> Your Job title is: {{ role }}</p>
        <p> Terms accepted: {{ terms }}</p>
        <p> People checked: {{ names }}</p>
        <p> TempSkill: {{ tempSkill }}</p>


    </div>
</template>

<script>
export default {
    data(){
        return{
            email: '',
            password: '',
            role: '',
            terms: false,
            names: [],
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        addSkill(e){
            if(e.key === ',' && this.tempSkill){
                if(!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill)
                }
                this.tempSkill = ''
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter((item) => {
                return skill !== item    
            })
            // console.log(this.skills)
        },
        handleSubmit(){
            // validate password
            this.passwordError = this.password.length > 5 ? 
                '' : 'Password must be at least 6 Characters'; 
            if(!this.passwordError){
                console.log('email:', this.email )    
                console.log('password:', this.password )    
                console.log('role:', this.role )    
                console.log('skills:', this.skills )    
                console.log('terms:', this.terms )    
            }
        },    
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
    input[type="checkbox"]{
        display: inline-block;
        width: 16px;
        margin: 0 10px 0 0;
        position: relative;
        top: 2px;
    }
    .pill{
        display: inline-block;    
        margin: 20px 10px 0 0;
        padding: 6px 12px;
        background: green;
        border-radius: 20px;
        font-size: 12px;
        letter-spacing: 1px;
        font-weight: bold;
        color: white;
        cursor: pointer;
    }
    button {
        background: #0b6dff;
        border: 0;
        padding: 10px 20px;
        margin-top: 20px;
        color: white;
        border-radius: 20px;
    }
    .submit {
        text-align: center;
    }
    .error {
        color: #ff0062;
        margin-top: 10px;
        font-size: 0.8em;
        font-weight: bold;
    }


</style>