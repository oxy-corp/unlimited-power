<script lang="ts">
    import { PowerBoosts } from "../gamelogic/upgrades";
    import PowerBoost from "./powerBoost.svelte";
 </script>
 
 <!-- Layout for a list of generator upgrades -->
 <div>
    <h2>Power Boosts</h2>
    {#each PowerBoosts as PowerBoosts}
       <PowerBoost {PowerBoosts} />
    {/each}
 </div>
 
 <style>
 </style>