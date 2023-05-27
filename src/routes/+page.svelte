
<script lang="ts">

	type Activity = {
		endTime: number;
		startTime: number;
		name: string;
		totalTime: number;
	}

	const localStorageKey = 'activities';
	let activityFomLocalstorage = localStorage.getItem("activities");
	let activities: Activity[] = JSON.parse(activityFomLocalstorage  ?? "[]");

	function addActivity(){
		activities = [...activities, {startTime: 0, endTime: 0, totalTime: 0, name: ""}]
	}

	function startActivity(index: number){
		activities[index].startTime = new Date().valueOf()
		activities = activities;
		localStorage.setItem(localStorageKey, JSON.stringify(activities))
	}

	function endActivity(index: number){
		activities[index].endTime = new Date().valueOf();
		activities[index].totalTime = activities[index].endTime-activities[index].startTime;
		activities = activities;
		localStorage.setItem(localStorageKey, JSON.stringify(activities))

	}

	// hint: try using the javascript slice method to do array manipulation; phind.com is your friend!
	function deleteActivity(index: number){

	}


</script>
<button on:click={addActivity}>Add Activity</button>
{#each activities as activity, index (activity)}
<div>
	Activity Name
	<input bind:value={activity.name}>

	<!--To only show one button at a time, you can look into svelte if statements-->
	<button on:click={() => startActivity(index)} >Start</button>
	<button on:click={() => endActivity(index)} >End</button>

	{(activity.totalTime / 1000).toFixed(2)}
</div>
{/each}


<style lang="postcss">
	input{
		@apply text-black
	}
</style>