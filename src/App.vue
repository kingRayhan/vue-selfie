<template>
    <div id="app">
        <h1 class="title">Vue Selfie</h1>
        <camera ref='webcam'></camera>
        <br>
        <button @click="take_selfie">Take Selfie</button>    
    </div>
</template>

<script>
import camera from 'vue-webcam';
import dl from 'downloadjs';
export default {
    components: { camera },
    data () {
        return {
            photo: ''
        };
    },
    methods: {
        take_selfie()
        {
          var imageData = this.$refs.webcam.getPhoto();
          dl(imageData , 'selfie-' + Date.now() , 'image/jpeg');
        }
    }
};
</script>

<style scoped>
*{
  font-family: Arial;
}
.title{
  color: #42C562;
}
button{
  margin-top: 20px;
}
video{
  background-color: #DDD;
}
#app{
  text-align: center;
}
</style>