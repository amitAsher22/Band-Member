<template>
  <div>
    <h1>Band Member</h1>
    <table>
      <thead>
      <tr>
        <th v-for="title in tableHeader" :key="title">{{title}}</th>
      </tr>
      </thead>
      <tbody>
        <MemberRow v-for="(people,index) in members" :key="index+'r'" :people="people" :index="index" @delete="deletePeople" />
      </tbody>
    </table>
    <div class="addMember">
      <h2>Add brand member</h2>
      <p><strong>First Name:</strong></p>
      <input v-model="NewMember.first">
      <p><strong>Last Name:</strong></p>
      <input v-model="NewMember.last">
      <p><strong>Instrument:</strong></p>
     <select name="instrument" v-model="NewMember.instrument">
       <option v-for="instrument in instrumentOptions" :key="instrument">{{instrument}}</option>
     </select><br/><br/>
      <button class="Add" @click="AddMember()">Add</button>
    </div>
  </div>
</template>

<script>
import MemberRow from "@/components/MemberRow";
export default {
  name: "AddMembers",
  components:{MemberRow},
  data() {
    return {
      tableHeader:["First Name", "Last Name", "Instrument"],
      instrumentOptions:['bass','Electric guitar','Acoustic guitar','drums','flute'],
      members: [
        {
          first: 'John',
          last: 'Lennon',
          instrument: 'Electric guitar'
        },
        {
          first: 'Georg',
          last: 'Harrison',
          instrument: 'Acoustic guitar'
        },
        {
          first: 'amit',
          last: 'asher',
          instrument: 'Acoustic guitar'
        }
      ],
      NewMember:{
        first:'',
        last:'',
        instrument:''
      }
    }
  },
  methods: {
    AddMember: function () {
      if (this.NewMember.first && this.NewMember.last && this.NewMember.instrument) {
        this.members.push(this.NewMember)
        this.NewMember = {}
      } else {
        alert('all fields must be fill ')
      }
    },
    deletePeople: function (index, number, string) {
      console.log(index, number, string)
      this.members.splice(index, 1)
    }
  }
}
</script>

<style scoped>
body{
  font-family:'Source Sans Pro', sans-serif; ;
}
h1{
  text-align: center;
}
table{
  margin: auto;
  border-collapse: collapse;
}
th, td{
  padding: 8px;
}
th{
  border-bottom: black solid 1px;
}
.addMember{
  background-color: rgba(199, 198, 198, 0.46);
  text-align: center;
  width: 40%;
  margin:  auto;
}


.Add{
  color: white;
  background-color: #1515ee;
}
.Add:hover{
  color: black;
  background-color:white;
}
input {
 padding: 5px;
  border: none;
  border-radius: 20px;
  outline: none;


}
</style>