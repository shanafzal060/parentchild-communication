<template>
  <form @submit.prevent="submitData">
    <div>
      <label for="">Name:</label>
      <input type="text" placeholder="Enter your good name"  v-model="enteredName"/>
    </div>
    <div>
      <label for="">Phone:</label>
      <input type="tel" placeholder="Enter phone number" v-model="enteredPhone" />
    </div>
    <div>
      <label for="">Email:</label>
      <input type="email" placeholder="Enter email" v-model="enteredEmail" />
    </div>
    <div>
      <button>ADD CONTACT</button>
    </div>
  </form>
</template>

<script>
export default {
    emit:['add-contact'],
  data() {
    return {
      enteredName: "",
      enteredPhone: "",
      enteredEmail: "",
    };
  },
  methods:{
    submitData(){
        this.$emit('add-contact',this.enteredName,this.enteredPhone,this.enteredEmail)
    }
  }
};
</script>
