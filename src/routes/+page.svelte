<script>
	import { goto } from '$app/navigation'
	import { check_session } from '$lib/pocketbase/user'
	import { onMount } from 'svelte'
	/* TODO: Add site counting logic per account see /src/routes/dashboard/sites/+page.svelte? */
	onMount(async () => {
		if (await check_session()) {
			if (sites?.length) {
				await goto('/admin/dashboard/sites', { replaceState: true })
			} else {
				await goto('/admin/site', { replaceState: true })
			}
		} else {
			await goto('/admin/auth', { replaceState: true })
		}
	})
</script>
