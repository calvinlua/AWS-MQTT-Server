<script >
export default{
  name: 'HelloWorld',
  props: { msg:String },
  data(){
    return{
      message: null
    }
  },

  methods: {
    
publish(message) {
this.message = message;
this.mqtt = new Paho.Client ("3.0.18.123",9001,"vueClient");
this.mqtt.connect({mqttVersion: 3, userName:"user2", password:"password2",onSuccess: this.onConnect});
}   ,
onConnect(){
  this.mqtt.publish("light/test",this.message);
}
,
light_on() {
  this.publish("Lights On")
}
,
light_off() {
  this.publish("Lights Off")
}
}
}
</script>

<template>
  <h1>{{ msg }}</h1>

 
  <div class="card">
    <button type="button" @click="light_on">Trigger On</button>
    <button type="button" @click="light_off">Trigger off</button>
  </div>
    
  <p>
    Check out
    <a href="https://vuejs.org/guide/quick-start.html#local" target="_blank"
      >create-vue</a
    >, the official Vue + Vite starter
  </p>
  <p>
    Install
    <a href="https://github.com/johnsoncodehk/volar" target="_blank">Volar</a>
    in your IDE for a better DX
  </p>
  <p class="read-the-docs">Click on the Vite and Vue logos to learn more</p>
</template>

<style scoped>
.read-the-docs {
  color: #888;
}
</style>
