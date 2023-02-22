<template>
  <HelloWorld/>
  <button @click="login">Einloggen mit Google</button>
  <button @click="logout">AUSLOGGEN</button>
  <h1>{{ msg }}</h1>
  <button @click="status">Aktualisieren</button>
</template>

<script>
  import HelloWorld from './components/HelloWorld.vue';
  export default {
    name: 'App',
    components: {
      HelloWorld
    },
    data(){
      return{
        msg:"aha",
        user:auth.currentUser
      }
    },
    methods:{
      status(){
        if(this.user !== null){
          this.msg="eingelogt"
        }else{
          this.msg="ausgelogt"
        }
      },
      login(){
        signInWithPopup(auth,provider)
          .then((result)=>{
            this.user = result.user
          })
      },
      logout(){
        signOut(auth)
        .then((result)=>{
          this.user=null
        })
      }
    }
    

  }
  import { initializeApp } from "firebase/app";
  import { getAuth, signOut, GoogleAuthProvider, signInWithPopup } from "firebase/auth";
  import { getAnalytics } from "firebase/analytics";
  const firebaseConfig = {
    apiKey: "AIzaSyCVWJXA9U1dmMy0k9TlfS2owL1xGygN8uQ",
    authDomain: "ratatouille4.firebaseapp.com",
    projectId: "ratatouille4",
    storageBucket: "ratatouille4.appspot.com",
    messagingSenderId: "1077823290146",
    appId: "1:1077823290146:web:a715795b76b4f91ad6c37b",
    measurementId: "G-3R4JTPDDRJ"
  };

  const app = initializeApp(firebaseConfig);
  const auth = getAuth(app);
  const provider = new GoogleAuthProvider();
  const analytics = getAnalytics(app);

</script>