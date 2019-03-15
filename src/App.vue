<template>
  <div id="app">   
<div class="form1">
  <h1>SURVEY  FORM</h1>
  <p><font-awesome-icon icon="coffee" size="lg" /></p>
<b-row align="center"> 
 <b-form @submit="onSubmit" @reset="onReset" v-if="show">
      <b-form-group
        id="exampleInputGroup1"
        label="Email address:"
        label-for="exampleInput1"
        description="We'll never share your email with anyone else."
      >
      <b-form-input
          id="exampleInput1"
          type="email"
          v-model="form.email"
          required
          placeholder="Enter email" />
      </b-form-group>
      <b-form-group id="exampleInputGroup2" label="Your Name:" label-for="exampleInput2">
        <b-form-input
          id="exampleInput2"
          type="text"
          v-model="form.name"
          required  
          placeholder="Enter name" />
      </b-form-group>

      <b-form-group id="exampleInputGroup3" label="Food:" label-for="exampleInput3">
        <b-form-select id="exampleInput3" :options="foods" required v-model="form.food" />
      </b-form-group>

      <b-form-group id="exampleGroup4">
        <b-form-checkbox-group v-model="form.checked" id="exampleChecks">
          <b-form-checkbox value="me">Check me out</b-form-checkbox>
          <b-form-checkbox value="that">Check that out</b-form-checkbox>
        </b-form-checkbox-group>
      </b-form-group>
      <b-button type="submit" variant="primary">Submit
       
      </b-button>
      <b-button type="reset" variant="danger">Reset</b-button>
    </b-form>
</b-row>
</div>
<div class="ions">
     <footer>
    <ShareFacebook url="http://recruit.istyle.co.jp/career/"/>
    <ShareTwitter url="http://recruit.istyle.co.jp/career/"/>
    <ShareGooglePlus url="http://recruit.istyle.co.jp/career/"/>
    <ShareHatena url="http://recruit.istyle.co.jp/career/"/>
    <ShareLine url="http://recruit.istyle.co.jp/career/"/>
    </footer>
</div>
</div>
</template>

<script>
 import { ShareFacebook, ShareTwitter, ShareGooglePlus, ShareHatena, ShareLine } from 'vue-share-social'

export default {
  name: 'app',
  components: {
    ShareFacebook,
    ShareTwitter,
    ShareGooglePlus,
    ShareHatena,
    ShareLine
  },
  data() {
    return {
      showDismissibleAlert: false,
     form: {
          email: '',
          name: '',
          food: null,
          checked: []
        },
        foods: [{ text: 'Select One', value: null }, 'Carrots', 'Beans', 'Tomatoes', 'Corn'],
        show: true,
      }
  },
   methods:{
     handleClick(){
       this.showDismissibleAlert = true
     },

     onSubmit(evt) {
        evt.preventDefault()
        alert(JSON.stringify(this.form))
    },
      onReset(evt) {
        evt.preventDefault()
        /* Reset our form values */
        this.form.email = ''
        this.form.name = ''
        this.form.food = null
        this.form.checked = []
        /* Trick to reset/clear native browser form validation state */
        this.show = false
        this.$nextTick(() => {
          this.show = true
        })
      },
     
   } 
}
</script>
<style>
.form1 {
  padding-left:40%;
  padding-top: 10%;
}
.ions{
    padding-left: 80%
}
.h1{
 text-align:center;
 color:grey;
 text-shadow: 10%;

}
.p{
  text-align: center
}
</style>

