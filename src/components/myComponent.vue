<template>
  <div class="root">
    <div class="container">
      <div class="form-floating mb-3 mt-2">
        <input type="text"
               class="form-control"
               id="floatingInput"
               placeholder="Enter you name"
               v-on:input="handleName"
               v-bind:value="name"
               v-on:keypress.enter="addContact">
        <label for="floatingInput">Your Name</label>
        <button type="button" class="btn btn-warning mt-2" v-on:click="addContact" >Create contact</button>
      </div>
    </div>
    <div class="container">
      <div class="row">
        <div class="col-md-4" v-for="(item,index) in needTolist" :key="item.message">
            <div class="card mt-4" style="width: 18rem;">
              <div class="card-body">
                <h5 class="card-title">{{ item.message }}</h5>
                <p class="card-text">User descr Email phone address </p>
              </div>
              <button
                  type="button"
                  class="btn btn-danger "
                  v-on:click="needTolist.splice(index,1)">Delete</button>
            </div>
        </div>
      </div>
    </div>
  </div>




</template>

<script>
export  default {
  name:'myComponent',
  data(){
      return{
        name:"",
        needTolist:[]


      }
  },
  methods:{
    handleName(event){
      this.name=event.target.value;
      console.log(this.name);

    },


    addContact(){

      console.log(this.name);


      if(this.name===''){
        return;
      }
      this.needTolist.push({
        message: this.name
      })

      this.name='';


    }

  }
}

</script>