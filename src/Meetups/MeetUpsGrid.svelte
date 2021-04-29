<script>
    import MeetupItems from './MeetupItems.svelte';
    export let meetups;
</script>

<section id="meetups">
	{#each meetups as mymeetups}
		<MeetupItems
        id = {mymeetups.id}
        title = {mymeetups.title} 
		subtitle = {mymeetups.subtitle} 
		description = {mymeetups.description}
		imageUrl = {mymeetups.imageUrl} 
		contactEmail = {mymeetups.contactEmail}
		address = {mymeetups.address}
        isfav={mymeetups.isFavorite}
        on:click />
	{/each}
</section>

<style>
    section {
        width : 100%;
        display: grid;
        grid-template-columns: 1fr;
        grid-gap : 1rem; 
    }

    @media (min-width : 768px) {
        section {
            grid-template-columns: repeat(2, 1fr);
        }
    }
</style>