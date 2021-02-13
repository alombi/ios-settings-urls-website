<script>
   import { url } from '../selected.js';
   function closeModal(){
      var page = document.getElementById('page');
      var modal = document.getElementById('modal');
      page.style.display = 'block';
      modal.style.display = 'none';
   }
</script>

<div class="close_modal">
   <a on:click={closeModal}><ion-icon name="close-circle"></ion-icon></a>
</div>
<h1>{$url.key}</h1>
<code>{$url.value}</code>


<style>
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