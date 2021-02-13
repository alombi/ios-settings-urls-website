<script>
import { onMount } from 'svelte';

   import {meta} from 'tinro';
   const route = meta(); 
   let active;
   function change(param){
      active = param
   }
   onMount(()=>{
      if(route.url == '/'){
         var param = 'home'
         change(param)
      }else{
         var param = 'about'
         change(param)
      }
   })
</script>

<div class="navbar">
   <a class:active="{active == 'home'}" on:click={()=>{change('home')}} id="home" href="/">Home</a>
   <a class:active="{active == 'about'}"  on:click={()=>{change('about')}} id="about" href="/about">About</a>
   <a href="https://github.com"><ion-icon name="logo-github"></ion-icon></a>
</div>

<style>
   ion-icon{
      font-size: 24px;
      margin: 0px 0px 6px 0px;
   }
   a{
      margin-left: 2px;
      margin-right: 2px;
      border-radius: 9px;
      padding-top:12px;
      padding-bottom:0px;
      padding-left:20px;
      padding-right:20px;
      text-decoration: none;
      color:#80CFFB;
      background-color: #FFFFFF;
   }
   .active{
      background-color: #F2F2F6;
   }  
   @media(prefers-color-scheme: dark){
      a{
         background-color: #1C1C1D;
      }
      .active{
         background-color: #2D2C2E;  
      }
   }
</style>