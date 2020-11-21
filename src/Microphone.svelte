<script>
    var globalStream;
    let buttonNotClicked = true;
    function startStream(constraints) {
        navigator.mediaDevices.getUserMedia(constraints)
        .then(function(stream) {
            globalStream = stream
            })
        .catch(function(err) {
            console.log(err)
            });
        buttonNotClicked = false 
        return
}
    function stopStream() {
        globalStream.getTracks().forEach(function(track) {
            track.stop();
        });
        return
    }

    function process(steam) {
        a = 'a'
    }

</script>

<main>
    {#if buttonNotClicked}
    <button on:click={startStream({audio:true, video:false})}>
       Start 
    </button>
    {/if}
</main>

<style>
    button {
        margin-top: 10px;
		margin-left: 50px;
        padding: 10px;
        border-color: 0.0px solid #EFEFEF;
        background-color: white;
		font-family: 'geometria';
        display: inline-block;
        border-radius: 15px;
		box-shadow: 0px 0px 50px rgba(0,0,0,0.05)
    }

</style>