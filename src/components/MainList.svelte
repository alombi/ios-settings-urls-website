<script>
   import { onMount } from 'svelte';
   import URLBlock from './URLBlock.svelte';
	let keys = [];
	let temporary = [];
	let values = [];
	let list = [];
	let params, promise;
	async function reset(){
		let request = await fetch('https://raw.githubusercontent.com/FifiTheBulldog/ios-settings-urls/master/settings-urls.md')
		let response = await request.text();
		response = response.replace('# Settings URLs\n\n', '');
		response = response.split('\n');
		response.pop()
		list = response
		for(var i = 0; i < response.length; i++){
			keys.push(response[i].split(':')[0].replace('- ', ''));
			keys = keys
			sessionStorage.setItem('keys', JSON.stringify(keys));
			if(response[i].split(':')[2].indexOf('or') != -1){
				var value = response[i].split(':')[1] + ':' + response[i].split(':')[2];
				value = value.split(' or ',)[0];
				value = value.replaceAll('\`', '')
				values.push(value);
				values = values
			}else{
				var value = response[i].split(':')[1] + ':' + response[i].split(':')[2];
				value = value.replaceAll('\`', '')
				values.push(value);
				values = values
			}
		}
		let done = true;
		return done
	}
	async function search(){
		keys.length = 0;
		keys = JSON.parse(sessionStorage.getItem('keys'));
		for(var i = 0; i < values.length; i++){
			if(keys[i].toUpperCase().indexOf(params.toUpperCase()) != -1){
				temporary.push(keys[i]);
				temporary = temporary;
			}
		}
		keys = [];
		keys = temporary;
	}

	function clear(){
		var searchField = document.getElementsByTagName('input')[0]
		searchField.value = '';
		params = '';
		search();
	}
	function key(e){
		if(e.keyCode == 13){
			search()
		}
	}
onMount(()=>{
	promise = reset()
})
</script>

<div>
	<a id="search" on:click={search}><ion-icon name="search"></ion-icon></a><input on:keypress={key} placeholder="Search" type="text" bind:value={params}><a id="x"><ion-icon on:click={clear} name="close-outline"></ion-icon></a>
	<br><br>
	<hr>
	<br>
	<div class="container">
		{#await promise}
			<div class="loader"></div>
		{:then done}
		{#if keys.length != 0}
	<div class="grid">
			{#each keys as key}
				<URLBlock key={key} values={values} />
			{/each}
	</div>
		{:else}
			<p>No results!</p>
		{/if}
		{/await}
	</div>
	<br>
	<p id="footer">© 2021 alombi - Developed and designed by alombi - URLs Collection by u/FifiTheBulldog</p>
</div>

<style>
	hr{
		border:0.3px solid #E5E5EA
	}
	#search{
		margin-right:-5px;
	}
	#x{
		margin-left:10px;
	}
	@media(prefers-color-scheme: dark){
		hr{
			border: 0.3px solid #2D2C2E;
		}
	}
</style>