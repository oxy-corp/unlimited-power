<script lang="ts">
    import { gameModel } from "../gamelogic/gamemodel";
    import type { powerBoost } from "../gamelogic/upgrades";
    import { formatNumber, formatWhole } from "../gamelogic/utils";
    export let PowerBoost: powerBoost;
 
    // some svelte magic that means whenever the gameModel is updated we will refresh this PowerBoost
    $: $gameModel, (PowerBoost = PowerBoost);
 
    function purchase() {
       PowerBoost.purchase();
 
       // setting the pBoost to itself will cause the component to update
       PowerBoost = PowerBoost;
    }
 </script>
 
 <!-- The layout for a single PowerBoost upgrade -->
 <div>
    <strong>{PowerBoost.name}</strong>
    <span>owned: <strong>{formatWhole(PowerBoost.getTotalCount())}</strong></span>
    <button on:click={purchase}>Buy for ${formatNumber(PowerBoost.getPrice(), 2)}</button>
    <p>{PowerBoost.description}</p>
 </div>
 
 <style>
    div {
       margin-bottom: 1rem;
       padding: 0.5rem;
       border: 1px solid #ccc;
    }
    p {
       margin: 0.5em 0;
    }
 
    button {
       float: right;
    }
 </style>
 