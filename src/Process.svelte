<script lang="ts">

    import Progress from './Progress.svelte';
    export let activeUsers:number;
    export let time;
    export let processesLength: number;
    export let process: any;

</script>

<main>
        <Progress {time} >
            <div>
                <p>
                    {process.name}
                </p>
                <p>
                    Local:{(100/processesLength).toFixed(2)}
                </p>
                <p>
                    Global:{(100/(activeUsers*processesLength)).toFixed(2)}
                </p>
            </div>
        </Progress>
</main>






<style>
	main {
		text-align: center;
		padding: 1em;
		max-width: 240px;
		margin: 0 auto;
        background-color:tomato;

	}

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
	}

</style>