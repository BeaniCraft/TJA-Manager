<script>
  import { Tabs } from '@skeletonlabs/skeleton-svelte';

  // Images
  import iconUrl from '$lib/images/icon.png'

  // Lucide icons

  // Tab state
  let group = $state('about');
</script>

<!-- Content -->
<Tabs value={group} onValueChange={(e) => (group = e.value)} listJustify="justify-center">
  {#snippet list()}
    <Tabs.Control value="about">About TJAMGR</Tabs.Control>
    <Tabs.Control value="credits">Credits</Tabs.Control>
    <Tabs.Control value="licenses">Licenses</Tabs.Control>
  {/snippet}
  
  {#snippet content()}
    <Tabs.Panel value="about">
      <div class="flex card p-4">
        <img src={iconUrl} alt="TJAMGR icon">
                
        <div class="relative w-full">
        <h1><b>TJAMGR:</b> A hassle free tool to manage .TJAs.</h1>
                
        <hr>

        <p>Current version:</p>

        <p class="absolute bottom-0"><b>BeaniCraft <span class="text-primary-400">|</span> 2025</b></p>
      </div>
    </div>

    </Tabs.Panel>
          
    <Tabs.Panel value="credits">

    </Tabs.Panel>
          
    <Tabs.Panel value="licenses">

    </Tabs.Panel>
  {/snippet}
</Tabs>

<style>

</style> 