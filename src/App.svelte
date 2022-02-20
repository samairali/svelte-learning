<script>
	import Form from './Components/Form.svelte';
	import Modal from './Components/Modal.svelte';
	import PersonsLoop from './Components/Persons_loop.svelte';
	import Header from './Components/Header.svelte';
	export let name;
	let openModal = false;
	let person = {} ;
	const toggleModal = () => {
		openModal = !openModal
	}
	const addPersonCustomEvent = (e) => {
		person = e.detail;
		console.log(person)
		// PersonsLoop.set({personData: person})
		
	}
</script>

<main>
	<Header />
	<button on:click={() => {toggleModal()}}>open modal</button>
	<section>
		<PersonsLoop bind:personData={person} />
	</section>
</main>
<Modal isPromo={true} body="main modal here" openModal={openModal} on:click={() => {toggleModal()}}  >
	<Form on:addPerson={addPersonCustomEvent} />
</Modal>