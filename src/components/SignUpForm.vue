<template>
 <div class="container mt-5 ">
     <div class="row justify-content-center">
         <div class="col-8">
             <h1 class="display-5 mb-5">sign-up</h1>
            <form class="formWrapper p-5" @submit.prevent="handleSubmit">
                <div class="mb-3">
                    <label for="exampleInputEmail1" class="form-label">Email address</label>
                    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" required v-model="email">
                </div>
                <div class="mb-3">
                    <label for="exampleInputPassword1" class="form-label">Password</label>
                    <input type="password" class="form-control" id="exampleInputPassword1" required v-model='password'>
                    <div class="text-danger" v-if="passwordError">{{passwordError}}</div>
                </div>
                <label for="selectRole" class="form-label">Role</label>
                <select id="selectRole" class="form-select" aria-label="Default select example" v-model="role">
                    <option value="developer">web developer</option>
                    <option value="designer">web designer</option>
                </select>
                <div class="mb-3">
                    <label for="skills" class="form-label mt-3">Skills</label>
                    <input type="text" class="form-control mb-2" id="skills" v-model="tempSkill" @keyup="addSkill">
                    <span class="mx-1 skill" v-for="skill in skills" :key="skill"><span @click="deleteSkill(skill)">{{skill}} <i class="fas fa-times text-danger fs-6"></i></span></span>
                </div>
                <div class="form-check mt-4">
                    <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" required v-model="terms">
                    <label class="form-check-label" for="flexCheckDefault">
                        Accept terms and conditions
                    </label>
                </div>
                <button class="mt-3 btn btn-primary">create account</button>
            </form>
            <div class="mt-5">
                <p>email: {{email}}</p>
                <p>password: {{password}}</p>
                <p>role: {{role}}</p>
                <p>terms accepted: {{terms}} </p>
                <p>skills: {{skills}}</p>
                

            </div>
         </div>
     </div>
 </div>

</template>

<script>
export default {
    data(){
        return{
            email: '',
            password: '',
            role:'',
            terms:false,
            tempSkill: '',
            skills: [],
            passwordError: ''
        }
    },
    methods: {
        addSkill(e){
            if(e.key === ' ' && this.tempSkill){
                if(!this.skills.includes(this.tempSkill)){
                    this.skills.push(this.tempSkill)
                }
                    this.tempSkill= ''
            }
        },
        deleteSkill(skill){
            this.skills = this.skills.filter(el => el != skill)
        },
        handleSubmit(){
            //validate password
            this.passwordError = this.password.length > 5 ? '' : 'la password deve essere almeno di 6 caratteri'
        }
    }
}
</script>

<style>
    .formWrapper{
        border: 1px solid black;
        border-radius: 10px;
    }

    .skill{
        background-color: rgb(243, 243, 243);
        border-radius: 10px;
        padding: 5px;
    }
</style>