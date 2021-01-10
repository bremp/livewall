<script>
	let status = "off";
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
				status = "on";
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
				<img
					class="d-block w-100"
					src="https://lh6.googleusercontent.com/-A0tXm8gjfMU/U08VDMRGtuI/AAAAAAAAvrI/IQEscTGZyJY/s1920-w1920-h1080-c/IMG_0293%2Bhe.jpg"
					alt="First slide" />
			</div>
			<div class="carousel-item">
				<img
					class="d-block w-100"
					src="https://lh3.googleusercontent.com/-1xZqgaRDIec/Tg1dMJq1vBI/AAAAAAAAALc/7m0Tpv2htVc/s1920-w1920-h1080-c/071227-4144-PtLomaReef.jpg"
					alt="Second slide" />
			</div>
			<div class="carousel-item">
				<img
					class="d-block w-100"
					src="https://lh3.googleusercontent.com/-36YdSRh6q9w/TgtZEChvrkI/AAAAAAAJA0M/zVvIUAdwQ3Q/s1920-w1920-h1080-c/976865336_a%2Bview%2Bof%2Bqueenstown.jpg"
					alt="Third slide" />
			</div>
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
