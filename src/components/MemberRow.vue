<template>
  <tr :data-index="index">
    <td  @dblclick="edit()"  v-if="!shouldShowInput">{{ people.first }}</td>
    <input v-if="shouldShowInput" v-model="inputVal" @focusout="focusInput()"/>
    <td  >{{ people.last }}</td>
    <td>{{ people.instrument }}</td>
    <button class="remove" @click="deleteRow(index)"><i class="fas fa-trash-alt"></i></button>
  </tr>
</template>

<script>
export default {
  name: "MemberRow",
  props:["people", "index" , "delete"],
  data(){
    return {
      shouldShowInput: false,
      inputVal: "",
      newName:''
    }
  },
  methods: {
    edit: function(){
      this.shouldShowInput= true
      this.inputVal = this.people.first
    },
    deleteRow: function(index){
      this.$emit('delete', index ,8,"amir")
    },
    focusInput:function (){
     this.newName = this.inputVal
      this.people.first = this.newName
      this.shouldShowInput = false
      if(this.people.first === ''){
        this.shouldShowInput=true
      }
    },
  },

}
</script>

<style scoped>
.remove{
  color: white;
  background-color: red;
}
.remove:hover{
  background-color: black;

}

</style>