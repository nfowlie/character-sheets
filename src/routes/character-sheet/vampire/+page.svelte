<script lang="ts">
	import Skill from '../../../components/skill.svelte';
	const skillsList: { [key: string]: string[] } = {
		physical: [
			'Athletics',
			'Brawl',
			'Craft',
			'Drive',
			'Firearms',
			'Larceny',
			'Melee',
			'Stealth',
			'Survival'
		],
		social: [
			'Animal Ken',
			'Etiquette',
			'Insight',
			'Intimidation',
			'Leadership',
			'Performance',
			'Persuasion',
			'Streetwise',
			'Subterfuge'
		],
		mental: [
			'Academics',
			'Awareness',
			'Finance',
			'Investigation',
			'Medicine',
			'Occult',
			'Politics',
			'Science',
			'Technology'
		]
	};
</script>

<div id="CharacterSheet">
	<h1>Vampire The Masquerade</h1>
	<div class="skills">
		<h2>Skills</h2>
		<div class="skills-list">
			{#each Object.keys(skillsList) as skillType}
				<div class="skill-type" data-skill-type={skillType}>
					{#each skillsList[skillType] as skill}
						<Skill skillPoints={5} skillName={skill}>
							<span slot="skill-name">{skill}</span>
						</Skill>
					{/each}
				</div>
			{/each}
		</div>
	</div>
</div>

<style>
	:root {
		--bg-color: hsl(33.75, 66.67%, 95.29%);
		--main-color: hsl(353.65, 76.47%, 26.67%);
	}
	#CharacterSheet {
		display: grid;
		justify-content: center;
		background-color: var(--bg-color);
	}
	#CharacterSheet > div {
		width: 75vw;
	}
	.skills {
		text-align: center;
	}
	h1 {
		text-align: center;
	}
	h2 {
		color: var(--main-color);
	}
	.skills-list {
		display: grid;
		grid-template-columns: repeat(3, 1fr);
		column-gap: 1rem;
		border-top: 2px solid var(--main-color);
		padding-top: 2rem;
	}
	.skill-type {
		display: grid;
		grid-template-columns: auto;
		row-gap: 1rem;
	}
</style>
