<script>
	import Header from "./UI/Header.svelte";
	import TopHeader from "./UI/TopHeader.svelte";
	import MeetUpsGrid from "./Meetups/MeetUpsGrid.svelte";   
	import Button from "./UI/Button.svelte";
	import EditMeetup from "./Meetups/EditMeetup.svelte";
	let meetups = [

		{	id : 'm1',
			title : 'HTML Bootcamp',
			subtitle : 'Learn HTML in just 2 Hours',
			description : 'In this meetup we learn how to define structure of web document by using HTML (Hypertext Markup Language)',
			imageUrl : 'https://i.pinimg.com/originals/73/1d/c3/731dc376f5b85513110afed2cf307803.png',
		    address : 'BLOCK- G Nerd Road , 2345 New York',
			contactEmail : 'info@test.com',
			isFavorite : false}, 
		{	id : 'm2',
			title : 'Coading Bootcamp',
			subtitle : 'Learn coding like a professional',
			description : 'In this meetup we will have soome experts that will teach you how to code like a professionals',
			imageUrl : 'https://www.goodcore.co.uk/blog/wp-content/uploads/2019/08/what-is-coding.png',
		    address : 'BLOCK- H City Road , 2245 New Delhi',
			contactEmail : 'code@test.com',
			isFavorite : false},
		];

		let editMode;
		function addMeetups (event){
			let newMeetups = {
				id : Math.random().toString(),
				title : event.detail.title,
				subtitle : event.detail.subtitle,
				address : event.detail.address,
				imageUrl : event.detail.imageUrl,
				contactEmail : event.detail.contactEmail,
				description : event.detail.description
			};
			meetups = [newMeetups, ...meetups];
			editMode = null;
		};

		function cancelEdit() {
			editMode =null;
		}
		function togglefavorite(event) {
			alert("Hello World!");
			const id =event.detail ;
			const updatedMeetup = { ...meetups.find(m => m.id === id) };
			updateMeetup.isFavorite = !updatedMeetup.isFavorite;
			const meetupIndex = meetups.findIndex(m => m.id === id);
			const updatedMeetups = [...meetups];
			updateMeetups[meetupIndex] = updatedMeetup;
			meetups = updatedMeetups;	
		}

</script>
<TopHeader />
<Header />

<main>
	<div class="meetup-controls">
		<Button on:click="{() => editMode = 'add'}" caption="New Meetup"/>
	</div>	
	{#if editMode === 'add'}
		<EditMeetup on:save="{addMeetups}" on:cancel={cancelEdit} />
	{/if} 
	<MeetUpsGrid meetups={meetups} on:click={togglefavorite}/>
</main>

<style>
main {
	margin-top : 6rem;
}	
.meetup-controls {
	margin : 1rem;
}
</style>