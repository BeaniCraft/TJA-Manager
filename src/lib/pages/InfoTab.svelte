<script>
  import { Tabs } from '@skeletonlabs/skeleton-svelte';

  // Images
  import iconUrl from '$lib/images/icon.png'

  // Lucide icons
  import { AppWindow } from 'lucide-svelte';
  import { BookText } from 'lucide-svelte';
  import { ScrollText } from 'lucide-svelte';

  // Tab state
  let group = $state('about');

  const getChangelog = async () => {
    let changelog = document.getElementById("changelog");
    
    const changelogurl = 'https://raw.githubusercontent.com/OpenTaiko/OpenTaiko-Hub/refs/heads/main/CREDITS.md'
    const changelogresponse = await fetch(changelogurl);
    const changelogdata = await changelogresponse.text();
    

    changelog.innerHTML = changelogdata;
  }
</script>

<!-- Content -->
<Tabs value={group} onValueChange={(e) => (group = e.value)} listJustify="justify-center">
  {#snippet list()}
    <Tabs.Control value="about">{#snippet lead()}<AppWindow/>{/snippet} About TJAMGR</Tabs.Control>
    <Tabs.Control value="changelog">{#snippet lead()}<BookText/>{/snippet} Changelog</Tabs.Control>
    <Tabs.Control value="credits-licenses">{#snippet lead()}<ScrollText/>{/snippet} Credits/Licenses</Tabs.Control>
  {/snippet}
  
  {#snippet content()}
    <Tabs.Panel value="about">
      <div class="flex card preset-outlined-surface-500 p-4">
        <img src={iconUrl} alt="TJAMGR icon">
                  
        <div class="relative w-full">
          <h1><b>TJAMGR:</b> A hassle free tool to manage TJAs.</h1>
          <hr>
          <p>Current version: [placeholder]</p>

          <p class="absolute bottom-0"><b>BeaniCraft <span class="text-primary-400">|</span> 2025</b></p>
        </div>
      </div>
    </Tabs.Panel>
    
    <Tabs.Panel value="changelog">
      <div class="flex card preset-outlined-surface-500 p-4">
        <div class="relative w-full">
          <h1><b>Changelog</b></h1>
          <hr>
          <button type="button" class="btn btn-sm preset-filled-primary-500" onclick={getChangelog}>get changelog</button>

          <p id="changelog"></p>
        </div>
      </div>
    </Tabs.Panel>
          
    <Tabs.Panel value="credits-licenses">
      <div class="flex card preset-outlined-surface-500 p-4">
        <div class="relative w-full">
          <h1><b>Credits/Licenses</b></h1>
          
          <hr>
          
          <h3>Software Credits</h3>
          
          <hr>
          
          <h3>Contributor Credits</h3>
          
          <hr>

        </div>
      </div>
    </Tabs.Panel>
  {/snippet}
</Tabs>

<style>

</style> 