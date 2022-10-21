<template>
  <li>
    <h2>{{ name }} {{isFavorite ? "(Favorite)" : "" }}</h2>
    <button @click="toggleFavorite">toggle Status</button>
    <button @click="toggleDetails">
      {{ detailsAreVisible ? "Hide" : "Show" }} Details
    </button>
    <ul v-if="detailsAreVisible">
      <li>
        <strong>phone:</strong>
        {{ phoneNumber }}
      </li>
      <li>
        <strong>Email:</strong>
        {{ emailAddress }}
      </li>
    </ul>
  </li>
</template>

<script>
export default {
  props: {
    id:{
        type:String,
        required:true
    },
    name: {
      type: String,
      required: true,
    },
    phoneNumber: {
      type: String,
      required: true,
    },
    emailAddress: {
      type: String,
      required: true,
    },
    isFavorite: {
      type: Boolean,
      required: false,
      default: false,
      // validator:function(value){
      //     return value === '1' || value === '0'
      // }
    },
  },
//   emits:['toggle-favorite'],
emits:{
  'toggle-favorite':function(id){
    if(id){
        return true;
    }else{
        console.log("Id is missing")
        return false;
    }
  }  
},
  data() {
    return {
    //   fav: this.isFavorite,
      detailsAreVisible: false,
    };
  },
  methods: {
    toggleDetails() {
      this.detailsAreVisible = !this.detailsAreVisible;
    },
    toggleFavorite() {
    //   this.fav = !this.fav;
     this.$emit('toggle-favorite',this.id)
    },
  },
};
</script>
