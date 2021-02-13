<script>
   import { url } from '../selected.js';
   import { getNotificationsContext } from 'svelte-notifications';
  const { addNotification } = getNotificationsContext();
   function closeModal(){
      var page = document.getElementById('page');
      var modal = document.getElementById('modal');
      page.style.display = 'block';
      modal.style.display = 'none';
   }
   function copyURL(){
      var URL = document.getElementById("url").innerText;
      var inp =document.createElement('input');
      document.body.appendChild(inp)
      inp.value = URL
      inp.select();
      document.execCommand('copy',false);
      inp.remove();

      addNotification({ text: 'Copied!', position: 'bottom-center', type:'success', removeAfter: 4000 })
   }
</script>

<div class="close_modal">
   <a on:click={closeModal}><ion-icon name="close-circle"></ion-icon></a>
</div>
<h1>{$url.key}</h1>
<code id="url">{$url.value}</code>
<br>
<button on:click={copyURL}>Copy URL</button>

<style>
   button{
      margin-top: 20px;
      padding-left: 20px;
      padding-right: 20px;
      background-color: #80CFFB;      
   }
   .close_modal a, code{
      font-size: 20px;
      background-color: #F2F2F7;
   }
   code{
      font-size: 17px;
      padding: 3px;
      word-wrap: break-word;
   }
   @media(prefers-color-scheme: dark){
      .close_modal a, code{
         background-color: #2C2C2E;
         color:white;
      }
   }
   
</style>