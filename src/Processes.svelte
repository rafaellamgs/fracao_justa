<script lang="ts">

    import {currentUsers} from "./stores";
    import Process from "./Process.svelte";

    export let user:any;
    export let activeUsers:any;

    let processes = [];
    let processCounter = 0;
    const defaultAnimationTime = 8;

    $: time = defaultAnimationTime/((100/(activeUsers*processes.length))/100);

    function removeProcess(event) {
        processes = processes.filter( process =>  process.id !== event )
        currentUsers.update((_users) => {
            _users[user.id] -= 1
            return _users
        })
	}

    function addProcess() {
        processCounter += 1;
        const id = Date.now();
        processes.push({
            name: `Process ${processCounter}`,
            id: `Process${id}`,
        })

        processes = processes;

        currentUsers.update((_users) => {
            _users[user.id] += 1
            return _users
        })

        setTimeout(function() {
            removeProcess(`Process${id}`)
        }, (time || defaultAnimationTime )*1000)

    }

</script>

<main>
    <button on:click="{addProcess}">Criar Processo</button>
    <div class="wrapper" >
        {#each processes as process}
            <Process {time}  {process} {activeUsers} processesLength={processes.length}/>
        {/each}
    </div>

</main>














<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
        background-color:tomato;

	}

    div.wrapper {
        display: grid;
        grid-gap: 10px;
        grid-template-columns: repeat(auto-fill, 100px);
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

</style>