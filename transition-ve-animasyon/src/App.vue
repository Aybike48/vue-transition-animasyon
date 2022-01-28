<template>
  <div class="container">
    <div class="row">
      <div class="col-md-6 col-md-offset-3">
        <h3>Animation ve Transition</h3>
        <hr>
        <button class="btn btn-primary" @click="show=!show">göster</button>
        <transition name="fade">
          <div class="alert-success" v-if="show">alert kutusu</div>
        </transition>
        <hr>
        <transition name="slide" type="animation" appear>
          <div class="alert-success" v-if="!show">alert kutusu</div>
        </transition>
        <hr>
        <button class="btn btn-warning" @click="ekle">ekleme yap</button>
        <ul class="list-group">
          <transition-group name="slide">
             <li class="list-group-item" :key="numara" v-for="(numara,index) in numaraList" @click="sil(index)"> liste elemanları numara: {{ numara }}   </li>
          </transition-group>                        
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data(){
    return {
      show:false,
      numaraList:[1,2,3,4,5]
    }
  },
  methods : {
    ekle(){
      this.numaraList.splice(0,0,this.numaraList.lenght+1);
      console.log(this.numaraList)
    },
    sil(index){
      this.numaraList.splice(index,1);
    }
    
  }

}
</script>

<style>
  .fade-enter{
    opacity:0;
  }
  .fade-enter-active{
    transition: opacity 1s;
  }
  .fade-leave{
    
  }
  .fade-leave-active{
    transition: opacity 1s;
    opacity:0;

  }
  .slide-enter{ 
    opacity:0;
  }
  .slide-enter-active{
    animation: slide-in 1s ease-out forwards;
    transition: opacity 1s;
  }
  .slide-leave{
    
  }
  .slide-leave-active{
    animation: slide-out 1s ease-out forwards;
    transition: opacity 3s;
    opacity:0;
    position: absolute;

  }
  .slide-move{
    transition: transform 1s;
  }
  @keyframes slide-in {
    from{
      transform:translateY(20px);
    }
    to{
      transform:translateY(0px);
    }

  }
  @keyframes slide-out {
    from{
      transform:translateY(0px);
    }
    to{
      transform:translateY(20px);
    }

  }



</style>
