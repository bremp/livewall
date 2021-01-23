<script>
	import { backgrounds } from "./backgrounds";
	let firstBackground = backgrounds.shift();
	let isSupported = false;
	if ("wakeLock" in navigator) {
		isSupported = true;
		console.log("Screen Wake Lock API supported 🎉");
	} else {
		console.log("Wake lock is not supported by this browser.");
	}

	if (isSupported) {
		// create a reference for the wake lock
		let wakeLock = null;

		// create an async function to request a wake lock
		const requestWakeLock = async () => {
			try {
				wakeLock = await navigator.wakeLock.request("screen");
				// change up our interface to reflect wake lock active
				console.log("Wake lock active!");
			} catch (err) {
				// if wake lock request fails - usually system related, such as battery
				console.log(`${err.name}, ${err.message}`);
			}
		}; // requestWakeLock()
		requestWakeLock();
	} // isSupported
</script>

<style>
</style>

<div class="container-fluid">
	<div
		id="wakeControls"
		class="carousel slide"
		data-ride="carousel"
		data-interval="60000">
		<div class="carousel-inner">
			<div class="carousel-item active">
				<img class="d-block w-100" src={firstBackground.url} alt="" />
			</div>
			{#each backgrounds as background}
				<div class="carousel-item">
					<img class="d-block w-100" src={background.url} alt="" />
				</div>
			{/each}
		</div>
		<a
			class="carousel-control-prev"
			href="#wakeControls"
			role="button"
			data-slide="prev">
			<span class="carousel-control-prev-icon" aria-hidden="true" />
			<span class="sr-only">Previous</span>
		</a>
		<a
			class="carousel-control-next"
			href="#wakeControls"
			role="button"
			data-slide="next">
			<span class="carousel-control-next-icon" aria-hidden="true" />
			<span class="sr-only">Next</span>
		</a>
	</div>
</div>
