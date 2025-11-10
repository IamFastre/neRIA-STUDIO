<script lang="ts">
	import { dev } from '$app/environment';
	import 'titchy/styles';
	import '@/styles/global.scss';

	import { injectAnalytics } from '@vercel/analytics/sveltekit';
	injectAnalytics({ mode: dev ? 'development' : 'production' });

	let { children } = $props();
</script>

{@render children?.()}
