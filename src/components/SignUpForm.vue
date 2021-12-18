<template>
 <div class="container mt-5 ">
     <div class="row justify-content-center">
         <div class="col-8">
             <h1 class="display-5 mb-5">sign-up</h1>
            <form class="formWrapper p-5">
                <div class="mb-3">
                    <label for="exampleInputEmail1" class="form-label">Email address</label>
                    <input type="email" class="form-control" id="exampleInputEmail1" aria-describedby="emailHelp" required v-model="email">
                </div>
                <div class="mb-3">
                    <label for="exampleInputPassword1" class="form-label">Password</label>
                    <input type="password" class="form-control" id="exampleInputPassword1" required v-model='password'>
                </div>
                <label for="selectRole" class="form-label">Role</label>
                <select id="selectRole" class="form-select" aria-label="Default select example" v-model="role">
                    <option value="developer">web developer</option>
                    <option value="designer">web designer</option>
                </select>
                <div class="form-check mt-4">
                    <input class="form-check-input" type="checkbox" value="" id="flexCheckDefault" required v-model="terms">
                    <label class="form-check-label" for="flexCheckDefault">
                        Accept terms and conditions
                    </label>
                </div>
                <div class="mb-3">
                    <label for="skills" class="form-label">Skills</label>
                    <input type="text" class="form-control" id="skills" v-model="tempSkill" @keyup="addSkill">
                    <span class="mx-1" v-for="skill in skills" :key="skill">{{skill}} |</span>
                </div>
                <button type="submit" class="mt-3 btn btn-primary">Submit</button>
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
        }
    }
}
</script>

<style>
    .formWrapper{
        border: 1px solid black;
        border-radius: 10px;
    }
</style>