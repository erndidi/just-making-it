<template>
  <div class="test">
    <h1>{{title}}</h1>
<input type="text" v-model="title"><br/>
     <ul>
       <li v-for="item in items" :key="item.id">{{item.idx}}</li>
     </ul>
    <button v-on:click="greet('hello again')">Say Greeting </button><br/>
    <input type="text" v-on:keyup="pressKey"><br/>
    <label>First Name:</label><input type="text" v-model="user.first_name"><br/>
    <label>Last Name:</label><input type="text" v-model="user.last_name"><br/>
    <h3>{{fullname}}</h3><br/>
    <h3>{{msg}}</h3>
  </div>
</template>

<script>
export default {
  name: 'Test ',
  props:{
            msg:{
              type:String,
              default:'foobar'          
            }
        },
  data(){
    return{
      title: 'Hello World',
     
      user:{
        first_name:'Joe',
        last_name:'Blow'
      },
      showName: false,
      items:[
        {idx:'Item One'},
        {idx:'Item Two'},
        {idx:'Item Three'},
        {idx:'Item Four'},
        {idx:'Item Five'}
      ]
    
    }
     
  },
    methods: {
        greet:function(greeting){
          alert(greeting)
        },
        pressKey:function(e){
          console.log(e.target.value)
        }
      },
    computed:{
      fullname: function(){
        return this.user.first_name+' '+this.user.last_name;
      }
    }

  
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
</style>