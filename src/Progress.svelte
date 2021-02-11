<script lang="ts">
    export let time: any;

    const animateIn = (a) => {

        return {
            duration: time*1000,
            css: t => {
                return `background-position: ${(1-t)*100}% 100%;`
            }
        };
    };

</script>

<main>

    <div class="Process" in:animateIn  >
        <slot></slot>
    </div>

</main>

<style>
	main {
		text-align: center;
		max-width: 240px;
		margin: 0 auto;
        background-color:tomato;

	}

    div.Process {
        min-width: 100px;
        min-height: 100px;
        background: linear-gradient(to right, limegreen 50%, #fff 50%);
        background-size: 200% 100%;
        box-shadow: 1px black;
    }

	@media (min-width: 640px) {
		main {
			max-width: none;
		}
    }
</style>