<script>
    export let data;
    import { onMount } from 'svelte';

    onMount(async () => {
        
        // console.log(data);
        document.documentElement.style.setProperty('--primary-col', data.data.info[0].primary_col);
        document.documentElement.style.setProperty('--secondary-col', data.data.info[0].secondary_col);
    
    });

    
</script>

{#if data.data.length <= 0}
    <h1>This team hasnt signed up yet! If you are this team and would like to you can go <a href="/signup">here</a> or you can tell them to sign up!</h1>
{/if}

<div class="main">
    <div class="pfp-div">
        <h1>Team {data.data.info[0].team_num}</h1>
        <img class="pfp" src="{data.data.info[0].pfp}" alt="pfp">
        <p class="description"> {data.data.info[0].description}</p>
    </div>

    <div class="all-links">

        {#each data.data.links as link}
            <div class="button-divs">
                <a href="{link.url}" target="_blank">
                    <button class="tree-buttons" id="redirectWebsite">
    
                        <div class="container">
                            <div class="grid1">
                                <img class="button-logo" src="{link.icon}" alt="button logo">
                            </div>
                            <div class="grid2">
                                <p class="tree-header">{link.title}</p>
                                <p class="bg-info">{link.description}</p>
                            </div>
                        </div>
                    </button>
                </a>
            </div>
        {/each}
        

    </div>
</div>




<style>
    :root {
        --primary-col: #3E7B27;
        --secondary-col: #85A947;
    }
    
    :global(html) {color: var(--primary-col);}
    :global(body) {margin:0px; background: var(--secondary-col);}
    

    .main {
        display: grid;
    }

    .description {
        font-family: 'Helvetica', 'Arial', sans-serif;
        color: white;

    }

    .all-links {
        align-self: center;
        justify-self: center;
    }

    .button-divs {
        width: 50vw;
        height: 100%;
        margin: auto;
        margin-top: 30px;
        margin-bottom: 30px;
        border-radius: 10px; 
    }

    @media (max-width: 800px) {
    .button-divs {
        width: 80vw;
    }
    }

    .bg-info {
        margin-top: 1vh;
        color: white;
        font-family: 'Helvetica', 'Arial', sans-serif;
    }

    .pfp-div {
        margin-top: 10vh;
        text-align: center;
        
    }

    .pfp {
        width: 200px;
        height: 200px;
        border-radius: 10px;
    }

    .tree-buttons {
        background: var(--primary-col);
        border-radius: 10px;
        border: none;
        cursor: pointer;
        transition: transform 0.2s ease; /* Smooth transition for scaling */
        box-shadow: 0 0 5px 0px black;


    }

    .tree-buttons:hover {
        transform: scale(1.01); /* Enlarge the button on hover */
    }
  
    .tree-buttons:active {
        transform: scale(0.99); /* Slightly shrink the button */
    }


    .tree-header {
        color: white;
        font-family: 'Helvetica', 'Arial', sans-serif;
        font-weight: bold;
    }

    .button-logo {
        width: 80px;
        height: 80px;
        border-radius: 5px;
    }

    .container {
        display: grid;
        grid-template-columns: .2fr 1fr; 
    }
  
</style>