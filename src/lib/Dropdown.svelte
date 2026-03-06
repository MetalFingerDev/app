<script lang="ts">
	import { DropdownMenu } from 'bits-ui';

	const categories: string[] = [
		'Top stories',
		'World',
		'Technology',
		'Business',
		'Culture',
		'Science',
		'Health'
	];
	const authors: { name: string; role: string }[] = [
		{ name: 'Asha Patel', role: 'Staff Writer' },
		{ name: 'Jonas Meyer', role: 'Senior Editor' },
		{ name: 'Lina Gómez', role: 'Feature Writer' }
	];

	let sortBy = $state('latest');
	let activeTopics = $state(['Technology']);
	let includeImages = $state(true);
	let savedOnly = $state(false);
</script>

<DropdownMenu.Root>
	<DropdownMenu.Trigger>Explore</DropdownMenu.Trigger>

	<DropdownMenu.Portal>
		<DropdownMenu.Content>
			<DropdownMenu.Group>
				<DropdownMenu.GroupHeading>Sections</DropdownMenu.GroupHeading>
				{#each categories as category (category)}
					<DropdownMenu.Item>{category}</DropdownMenu.Item>
				{/each}
			</DropdownMenu.Group>
			<DropdownMenu.Separator />

			<DropdownMenu.Group>
				<DropdownMenu.GroupHeading>Sort & filters</DropdownMenu.GroupHeading>

				<DropdownMenu.RadioGroup bind:value={sortBy}>
					<DropdownMenu.RadioItem value="latest">
						{#if sortBy === 'latest'}✅
						{/if}Latest
					</DropdownMenu.RadioItem>
					<DropdownMenu.RadioItem value="most-read">
						{#if sortBy === 'most-read'}✅
						{/if}Most read
					</DropdownMenu.RadioItem>
					<DropdownMenu.RadioItem value="recommended">
						{#if sortBy === 'recommended'}✅
						{/if}Recommended
					</DropdownMenu.RadioItem>
				</DropdownMenu.RadioGroup>

				<DropdownMenu.CheckboxGroup bind:value={activeTopics}>
					<DropdownMenu.GroupHeading>Topics</DropdownMenu.GroupHeading>
					<DropdownMenu.CheckboxItem value="Technology">Technology</DropdownMenu.CheckboxItem>
					<DropdownMenu.CheckboxItem value="Science">Science</DropdownMenu.CheckboxItem>
					<DropdownMenu.CheckboxItem value="Health">Health</DropdownMenu.CheckboxItem>
					<DropdownMenu.CheckboxItem value="Business">Business</DropdownMenu.CheckboxItem>
				</DropdownMenu.CheckboxGroup>

				<DropdownMenu.CheckboxItem bind:checked={includeImages}
					>Include images</DropdownMenu.CheckboxItem
				>
				<DropdownMenu.CheckboxItem bind:checked={savedOnly}>Saved only</DropdownMenu.CheckboxItem>
			</DropdownMenu.Group>

			<DropdownMenu.Separator />

			<DropdownMenu.Group>
				<DropdownMenu.GroupHeading>Authors</DropdownMenu.GroupHeading>
				{#each authors as a (a.name)}
					<DropdownMenu.Item>
						<div style="display:flex;flex-direction:column;">
							<strong>{a.name}</strong>
							<small>{a.role}</small>
						</div>
					</DropdownMenu.Item>
				{/each}
			</DropdownMenu.Group>

			<DropdownMenu.Separator />

			<DropdownMenu.Sub>
				<DropdownMenu.SubTrigger>More</DropdownMenu.SubTrigger>
				<DropdownMenu.Portal>
					<DropdownMenu.SubContent>
						<DropdownMenu.Item>Saved stories</DropdownMenu.Item>
						<DropdownMenu.Item>Newsletter signup</DropdownMenu.Item>
						<DropdownMenu.Item>Preferences</DropdownMenu.Item>
					</DropdownMenu.SubContent>
				</DropdownMenu.Portal>
			</DropdownMenu.Sub>

			<DropdownMenu.Separator />
			<DropdownMenu.Arrow />
		</DropdownMenu.Content>
	</DropdownMenu.Portal>
</DropdownMenu.Root>
