
<script lang="ts">
	type Activity = {
		endTime: number;
		startTime: number;
		name: string;
		totalTime: number;
	}

	let activityFomLocalstorage = localStorage.getItem("activities");
	let activity: Activity = JSON.parse(activityFomLocalstorage  ?? "{}");

	function startActivity(){
		activity.startTime = new Date().valueOf();
		localStorage.setItem('activities', JSON.stringify(activity))
	}

	function endActivity(){
		activity.endTime = new Date().valueOf();
		activity.totalTime = activity.endTime-activity.startTime;
		localStorage.setItem('activities', JSON.stringify(activity))
	}

	let count = 0;
	function updatecount(){
		count += 5;
	}
</script>

<div>
	Activity Name
	<input bind:value={activity.name}>
	<button on:click={startActivity} >Start</button>
	<button on:click={endActivity} >End</button>

	<!-- {activity.startTime}
	{activity.endTime} -->
	{(activity.totalTime / 1000).toFixed(2)}
</div>

{JSON.stringify(activity, null, 2)}

<style lang="postcss">
	input{
		@apply text-black
	}
</style>