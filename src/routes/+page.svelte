<script>
  import { Navigation } from '@skeletonlabs/skeleton-svelte';

  // Pages
  import BrowseTab from '$lib/pages/BrowseTab.svelte';
  import InfoTab from '$lib/pages/InfoTab.svelte';

  // Images
  import logoUrl from '$lib/images/logo.png';

  // Lucide icons
  import { House } from 'lucide-svelte';
  import { Globe } from 'lucide-svelte';
  import { Info } from 'lucide-svelte';

  import { WifiOff } from 'lucide-svelte';
  
  import { FolderSearch } from 'lucide-svelte';
  import { RefreshCw } from 'lucide-svelte';
    
  // Navigation state
  let value = $state('home');
</script>

<div class="grid h-screen w-full grid-cols-[auto_1fr]">
  <!-- Navigation -->
  <Navigation.Rail width="w-[72px]" {value} onValueChange={(newValue) => (value = newValue)}>
    {#snippet header()}
      <Navigation.Tile label="Home" id="home"><House/></Navigation.Tile>
      <Navigation.Tile label="Browse" id="browse"><Globe/></Navigation.Tile>
    {/snippet}
    
    {#snippet tiles()}
    <!-- Don't know why this breaks if this is deleted, but okay -->
    {/snippet}

    {#snippet footer()}
      <Navigation.Tile label="Info" id="info"><Info/></Navigation.Tile>
    {/snippet}
  </Navigation.Rail>
  
  <!-- Content -->
  <div class="p-3"> 
    {#if value === "home"}
      <div> 
        <img src={logoUrl} alt="TJAMGR logo" class="mx-auto mb-3">
        
        <hr>
        
        <div class="card p-4 preset-outlined-surface-500">
          <p>Welcome to TJA Manager!
          <br><a href="https://ese.tjadataba.se/" target="_blank">ese.tjadataba.se</a>

          <br><br><button type="button" class="btn btn-sm preset-filled-primary-500">placeholder or something idk</button>
          
          </p>
        </div>
      </div>
    {/if}
      
    {#if value === "browse"}
      <BrowseTab/>
    {/if}

    {#if value === "info"}
      <InfoTab/>
    {/if}
  </div>
</div>

<style>

</style> 