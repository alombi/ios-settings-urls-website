<script>
	import Modal from './components/Modal.svelte';
	import MainList from './components/MainList.svelte';
	import Navbar from './components/Navbar.svelte';
	import {Route} from 'tinro'; 
</script>

<main>
	<Route path="/">
		<div id="page">
			<Navbar />
			<h1>iOS Settings URLs</h1>
			<MainList />
		</div>
		<div id="modal">
			<Modal />
		</div>
	</Route>
	<Route path="/about">
		<Navbar />
		<h1>About</h1>
		<div class="about_text">
			<p>This project aims to make the <a href="https://github.com/FifiTheBulldog/ios-settings-urls">ios-settings-url</a> repo more easy to browse, since its great width. The <a href="https://github.com/FifiTheBulldog/ios-settings-urls">ios-settings-url</a> repo was created and is curated by <a href="https://github.com/FifiTheBulldog">FifiTheBulldog</a>. This website was designed and developed by <a href="https://alombi.xyz">alombi</a>.<br>FifiTheBulldog's project is a big collection of URL schemes for the iOS Settings app. These URLs can be used in Shortcuts, Scriptable or for lots of others scopes. </p>
		</div>
	</Route>
</main>

<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: none;
		margin: 0 auto;
	}
	h1 {
		font-size:50px;
		font-weight:300;
	}
	h2{
		font-size:40px;
		font-weight:300;
	}
	.about_text p, h2{
		text-align: left;
	}
	.about_text{
		padding-left:5%;
		padding-right:5%;
	}
	a{
		text-decoration: none;
      color:#80CFFB;
		padding:0px;
		background-color: unset;
	}
</style>