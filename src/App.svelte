<!-- src/App.svelte -->

<script>
	import { onMount } from 'svelte';
	import Nav from '../components/Nav.svelte';
	import { database } from './utils/firebase';
	import { ref, onValue } from 'firebase/database';
  
	let snips = [];  // Declare snips here
  
	onMount(() => {
	  const snipsRef = ref(database, "snips");
  
	  // Listen for changes in the "snips" node
	  onValue(snipsRef, (snapshot) => {
		const snipsArray = [];
		snapshot.forEach((childSnapshot) => {
		  const snipKey = childSnapshot.key;
		  const snipData = childSnapshot.val();
		  snipsArray.push({ id: snipKey, ...snipData });
		});
		snips = snipsArray;
	  });
	});
  </script>
  
  <style>
	.container {
	  padding-top: 50px;
	  align-items: center;
	  text-align: center;
	  max-width: 600;
	  margin: auto;
	}
  
	.snip-container {
	  margin-bottom: 10px;
	}
  
	.copy-input {
	  width: 200px;
	}
  </style>
  
  <!-- HTML template for the App page -->
  <div>
	<!-- Include the Nav component -->
	<Nav />
  
	<!-- The rest of your page content goes here -->
	<div class="container">
	  <h1>Hello</h1>
  
	  <!-- Display snips from Firebase -->
	  {#each snips as { id, name, content }}
		<div class="snip-container">
		  <!-- Create label for name -->
		  <a href={`edit.html?id=${id}`}>{name}</a>
  
		  <!-- Create input for content with initial value -->
		  <input bind:value={content} class="copy-input" />
		  <button>Copy</button>
		</div>
	  {/each}
	</div>
  </div>
  