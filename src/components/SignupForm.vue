<template>

    <form @submit.prevent="handleSubmit">

        <label>Email:</label>
        <input type="email" required v-model="email" pattern="^\S+?@\S+\.com">
        <label>Password:</label>
        <input type="password" required minlength="5" v-model="password">

        <label>Skills</label>
        <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
        <div v-for="skill in skills" :key="skill" class="pill">
         
             
            <span @click="deleteSkill(skill,$event)"> {{ skill }}</span>  
           </div>

         <div class="submit">
            <button>Crete an Account</button>
         </div>




    </form>

    <h3>Value of email input control is {{ email }}</h3>
    <h3>Value of password input control is {{ password }}</h3>

</template>

<script>

export default {

    data() { return {
        email: '',
        password: '',
        skills : [],
        tempSkill: ''
    }},
    methods: {
        addSkill(e) {
            if (e.key === ',' && this.tempSkill) {
                if (!this.skills.includes(this.tempSkill))
                    this.skills.push(this.tempSkill)
            }
            this.tempSkill = '';
        },
        deleteSkill(skill,e) {
           console.log("skill to delete is ",skill,"with event", e);
           this.skills = this.skills.filter((item) => item != skill)

        },
        handleSubmit(e) {
            console.log('form submitted with the following values');
            console.log(' >> email:', this.email);
            console.log(' >> password', this.password);
            console.log(' >> skills', this.skills);

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
    margin: 25px 0 25px;
    font-size: 0.6em;
    text-transform: uppercase;
    letter-spacing: 1px;
    font-weight: bold;
}

input {
    display: block;
    padding: 10px 6px;
    width: 100%;
    box-sizing: border-box;
    border: none;
    border-bottom: 1px solid #ddd;
    color: #555
}

.pill {

    display: inline-block;
    margin: 20px 10px 0 0;
    padding: 6px 12px;
    background: #eee;
    border-radius: 20px;
    font-size: 12px;
    letter-spacing: 1px;
    font-weight: bold;
    color: #777;
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
    text-align:center;
}




</style>