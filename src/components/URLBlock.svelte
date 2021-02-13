<script>
   import { url } from '../selected.js';
   export let key;
   export let values;
   let value;
   let keys = JSON.parse(sessionStorage.getItem('keys'));
   
   function showValue(){
      var index = keys.indexOf(key)
      var page = document.getElementById('page');
      var modal = document.getElementById('modal');
      page.style.display = 'none';
      modal.style.display = 'block';
      var urlObj = {
         'key':key,
         'value':values[index]
      }
      url.set(urlObj)
   }
</script>

<div class="item" on:click={showValue}>
   <h3>{key}</h3>
</div>