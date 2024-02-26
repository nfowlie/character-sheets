<script lang="ts">
	let skill: HTMLDivElement;
	let skillPoint: number = 0;
	export let skillPoints: number = 0;
	export let skillName: string = '';

	const checkBoxes = (sp: number) => {
		const spd: NodeListOf<HTMLInputElement> = skill.querySelectorAll('input[name="skillPoint"]');
		if (sp == skillPoint) {
			for (let s: number = 0; s < 5; s++) spd[s].checked = false;
		} else {
			for (let s = 0; s < 5; s++) {
				if (parseInt(spd[s].dataset.skillPoint || '') <= sp) {
					spd[s].checked = true;
				} else {
					spd[s].checked = false;
				}
			}
			skillPoint = sp;
		}
	};
</script>

<div class="skill" bind:this={skill}>
	<label for={skillName}><slot name="skill-name" /> </label><input type="text" name={skillName} />
	<span class="skill-points">
		{#each Array(skillPoints) as _, skillPoint}
			<label>
				<input
					type="checkbox"
					name="skillPoint"
					data-skill-point={skillPoint}
					on:change={() => checkBoxes(skillPoint)}
				/>
			</label>
		{/each}
	</span>
</div>

<style>
	.skill {
		display: flex;
		justify-content: space-between;
		gap: 0.25rem;
	}
	.skill > input {
		flex: 1 1 auto;
		width: 2rem;
	}
	.skill-points {
		display: flex;
	}
</style>
