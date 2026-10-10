<script lang="ts">
  let { name, size = 16 }: {name: string; size?: number} = $props();
</script>
<svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="1.85" stroke-linecap="round" stroke-linejoin="round" aria-hidden="true" style="flex-shrink:0">
{#if name === 'mail'}<rect x="2.5" y="4.5" width="19" height="15" rx="2"/><path d="m3 6 9 7 9-7"/>
{:else if name === 'phone'}<path d="M22 16.9v3a2 2 0 0 1-2.2 2 19.6 19.6 0 0 1-8.5-3 19.3 19.3 0 0 1-6-6 19.6 19.6 0 0 1-3-8.6A2 2 0 0 1 4.3 2h3a2 2 0 0 1 2 1.7l.6 3a2 2 0 0 1-.6 1.9L7.5 10a16 16 0 0 0 6.5 6.5l1.4-1.8a2 2 0 0 1 1.9-.6l3 .6a2 2 0 0 1 1.7 1.9Z"/>
{:else if name === 'linkedin'}<rect x="2" y="2" width="20" height="20" rx="2"/><path d="M7 10v7M7 7h.01M11 17v-7h3v1a3 3 0 0 1 6 2v4M11 10v7"/>
{:else if name === 'github'}<path d="M9 19c-4.4 1.4-4.4-2.5-6-3m12 6v-3.4a3 3 0 0 0-.9-2.3c3-.3 6.2-1.5 6.2-6.8a5.3 5.3 0 0 0-1.4-3.7 4.9 4.9 0 0 0-.1-3.7s-1.2-.4-3.8 1.4a13 13 0 0 0-7 0C5.4 1.7 4.2 2.1 4.2 2.1a4.9 4.9 0 0 0-.1 3.7 5.3 5.3 0 0 0-1.4 3.7c0 5.3 3.2 6.5 6.2 6.8A3 3 0 0 0 8 18.6V22"/>
{:else if name === 'globe'}<circle cx="12" cy="12" r="9"/><path d="M3 12h18M12 3c-5 5-5 13 0 18M12 3c5 5 5 13 0 18"/>
{:else if name === 'printer'}<path d="M6 9V3h12v6M6 18H4a2 2 0 0 1-2-2v-5a2 2 0 0 1 2-2h16a2 2 0 0 1 2 2v5a2 2 0 0 1-2 2h-2"/><path d="M6 15h12v7H6zM18 12h.01"/>
{:else if name === 'briefcase'}<rect x="2" y="7" width="20" height="14" rx="2"/><path d="M8 7V5a2 2 0 0 1 2-2h4a2 2 0 0 1 2 2v2M2 13c7 4 13 4 20 0"/>
{:else if name === 'database'}<ellipse cx="12" cy="5" rx="9" ry="3"/><path d="M3 5v14c0 4 18 4 18 0V5M3 12c0 4 18 4 18 0"/>
{:else if name === 'monitor'}<rect x="2" y="3" width="20" height="15" rx="2"/><path d="M8 22h8M12 18v4"/>
{:else if name === 'git'}<path d="m12 2 10 10-10 10L2 12 12 2ZM9 9l6 6M9 9v5M15 15v-5"/><circle cx="9" cy="9" r="1"/><circle cx="15" cy="15" r="1"/>
{:else if name === 'html'}<path d="M4 2h16l-1.5 18L12 22l-6.5-2L4 2Z"/><path d="M8 7h8m-8 5h8m-8-5 1 10 3 1 3-1 .5-5"/>
{:else if name === 'css'}<path d="M4 2h16l-1.5 18L12 22l-6.5-2L4 2Z"/><path d="M8 7h8l-.4 5H9l.5 5 2.5 1 3-1 .4-3"/>
{:else if name === 'javascript'}<rect x="2" y="2" width="20" height="20" rx="3"/><path d="M9 8v8a2 2 0 0 1-3 1m7-2c1 3 5 3 5 0 0-3-5-1-5-5 0-3 4-3 5-1"/>
{:else if name === 'typescript'}<rect x="2" y="2" width="20" height="20" rx="3"/><path d="M6 9h8m-4 0v9m5-2c2 2 5 1 5-1 0-3-5-1-5-4 0-2 3-3 5-1"/>
{:else}<path d="m8 7-5 5 5 5m8-10 5 5-5 5m-3-12-2 14"/>
{/if}
</svg>