
<script>
    async function fetchParagraph() {
    	let paragraph = await fetch('https://litipsum.com/api');
		let data = await paragraph.text();	
		var result = data.match( /[^\.!\?]+[\.!\?]+/g );
		var shortened = result.slice(0,5)
		return shortened.join(' ');
    };
let text = fetchParagraph();
</script>

<main>
    <!-- Title -->
    <h1>Text</h1>
    <!-- Load text content promise--> 
	{#await text}
		<p>...waiting</p>
	{:then text} 
		<div>
		<p>{text}</p>
		</div>
	{:catch error}
		<p style="color: red">There seems to be an issue :(</p>
	{/await}
</main>

<style>
    h1 {
		color: black;
		font-family: 'geometria';
		padding-left: 50px;
	}
    p {
		font-family: 'geometria'
	} 
	div {
		margin-left: 50px;
		margin-right: 50px;
		border: 1px solid #EFEFEF;
		padding: 15px; 
		display: inline-block;
		border-radius: 25px;
		box-shadow: 0px 0px 50px rgba(0,0,0,0.05);
	}
</style>