<template>
  <div class="users">
   <h1>Users</h1>
   <form v-on:submit="addUser">
<input type="text" v-model="newUser.name" placeholder="Enter name">
<br/>
<input type="text" v-model="newUser.email" placeholder="Enter email">
<br/>
<input type="submit" value="Submit">
   </form>
     <ul>
       <li v-for="user in users" :key="user.id">
         <input type="checkbox" v-model="user.contacted">
         <span :class="{contacted: user.contacted}">
         {{user.name}}: {{user.email}}
         </span><button v-on:click="deleteUser(user)">x</button>
      </li>
     </ul>
  
  </div>
</template>

<script>
export default {
  name: 'users',

  data(){
    return{
      newUser:{},
      users:[
              {
              id:1,
              name:'Joe Blow',
              email: 'jblow@gmail.com',
              contacted: true

              }, 
              {
                id:2,
                name:'John Doe',
                email: 'jdoe@gmail.com',
                contacted: false
              },
              {
                id:3,
                name:'Jim Snow',
                email: 'jsnow@gmail.com',
                contacted: false
              } 
            ]   

        }     
      },
    methods: {
        addUser: function(e){
          this.users.push(
            {
              name: this.newUser.name,
              email:this.newUser.email,
              contacted:false
            }
          )          
            e.preventDefault();
        },
        deleteUser:function(user){
            this.users.splice(this.users.indexOf(user),1);
            e.preventDefault();
        }

      },
   
  
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: block;
  margin: 0 10px;
  height: 30px;
    line-height: 30px;
}
a {
  color: #42b983;
}

.contacted{
  text-decoration-line: line-through
}
</style>