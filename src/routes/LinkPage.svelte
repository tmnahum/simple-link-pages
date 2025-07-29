<script lang="ts">
    import { beforeUpdate, onMount } from "svelte";
    import type { LinkPageData } from "./data";
    import { goto, invalidate, invalidateAll } from "$app/navigation";

    export let data: LinkPageData;


    function getFavicon(link: Exclude<LinkPageData["links"][number], "br">){
        const API_URL = "https://s2.googleusercontent.com/s2/favicons?sz=64&domain="

        const href = link?.href
        const faviconUrl = link?.faviconUrl

        if (!href) // return same as would a page with no favicon
            return `${API_URL}""`

        if (faviconUrl === "None"){
            return ""
        }

        if (faviconUrl === "Auto" || faviconUrl === "" || !faviconUrl) {
            
            return `${API_URL}${href}`
        }
        else {
            return link.faviconUrl
        }
    }

    // our pages favicon light/dark
    // todo: improve this so tht it shows up in bookmarks/etc instead of loading after the page is loaded
    onMount(()=>{
        if (typeof window == "undefined") return
        if (typeof data.favicon == "string" ) return
        function updateFavicon() {
            const favicon = document.querySelector('head > link[rel="icon"]')! as HTMLLinkElement;
            const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches
            // console.log("Updating favicon", prefersDark, favicon, data.favicon.light, data.favicon.dark)
            if (prefersDark) {
                favicon.href = data.favicon.dark;
            } else {
                favicon.href = data.favicon.light;
            }
        }

        window.matchMedia('(prefers-color-scheme: dark)').addEventListener('change', updateFavicon);
        updateFavicon();
        setTimeout(updateFavicon); // idk why but this is needed to make it work on firefox, don't feel like spending time to figure out why. 
        setTimeout(updateFavicon, 700); // just in case
    })

    function getCustomUrl() {
        return `${window.location.origin}/?data=${encodeURIComponent(JSON.stringify(data))}`
    }
    // 
    onMount(() => {
        if (typeof window == "undefined") return
        

        // TODO: add support to CreateYourOwn for dark/light mode URLs

        console.log("FORK THIS PAGE AT:")
        console.log(getCustomUrl())
        //@ts-ignore
        document.getElementById("edit-link")!.href = getCustomUrl()
    })


</script>

<svelte:window on:popstate={e => {
    // fixes a bug
    invalidateAll()
}}></svelte:window>

<main>
    <div>
        {#each data.links as link}
            {#if link === "br"}
                <span style = "margin-top: .75rem;" />
            {:else}
                <li>
                    <img src="{getFavicon(link)}" alt="icon" style="width: 32px; height: 32px">  
                    
                    <a 
                        href={link.href}
                        target="_parent"
                    >
                        <!-- setting target _parent currently makes zen open link in same tab instead of in preview -->
                        {link.title}
                    </a>
                </li>  
            {/if}        
        {/each}
    </div>
</main>
<a id="edit-link" class="edit-button" title="Edit this page" data-sveltekit-reload>
    <svg xmlns="http://www.w3.org/2000/svg" width="25" height="25" viewBox="0 0 24 24">
        <path fill="currentColor" d="M5 19h1.425L16.2 9.225L14.775 7.8L5 17.575zm-2 2v-4.25L16.2 3.575q.3-.275.663-.425t.762-.15t.775.15t.65.45L20.425 5q.3.275.438.65T21 6.4q0 .4-.137.763t-.438.662L7.25 21zM19 6.4L17.6 5zm-3.525 2.125l-.7-.725L16.2 9.225z" />
    </svg>
</a>

<svelte:head>
    <!-- TODO add full favicon support so it works in safari -->
    {#if typeof data.favicon === "string"}
        <link rel="icon" type="image/png" href="{data.favicon}" />
    {:else if typeof data.favicon === "object"}
        <link rel="icon" type="image/png" href="{data.favicon.dark}" />
        
        <link rel="icon" type="image/png" href="{data.favicon.dark}" media="(prefers-color-scheme: dark)" />
        <link rel="icon" type="image/png" href="{data.favicon.light}" media="(prefers-color-scheme: light)" />
    {/if}
    
    <title>{data.title || "Link Page"}</title>
</svelte:head>

<style>
    div {
        /* Center it when shorter than viewport, allow scrolling when taller */
        width: fit-content;
        max-width: 100%;
        margin-inline: auto;
        padding-block: 2rem;
        display: flex;
        flex-direction: column;
        gap: .75rem;
    }
    
    main {
        min-height: 100vh;
        display: flex;
        flex-direction: column;
        justify-content: center;
        overflow-y: auto;
    }

    div li {
        display: flex; 
        align-items: center;
    }
    
    .edit-button{
        position: fixed;
        bottom: 1rem;
        right: 1rem;
        padding: 0.5rem;
        display: flex;
        align-items: center;
        justify-content: center;
        text-decoration: none;
        z-index: 50;
        opacity: 0.7;
        transition: all 0.2s ease;
        background: none;
        border: none;
        cursor: pointer;
        -webkit-tap-highlight-color: transparent;
        color: black;
    }
    .edit-button,
    .edit-button:link,
    .edit-button:visited,
    .edit-button:hover,
    .edit-button:active,
    .edit-button:focus  {
        color: black;
    }
    
    @media (prefers-color-scheme: dark) {
        .edit-button:link,
        .edit-button:visited,
        .edit-button:hover,
        .edit-button:active,
        .edit-button:focus  {
            color: white;
        }
    }
    
    .edit-button:hover {
        opacity: 1;
    }
    
    div li {
        display: flex; 
        align-items: center; 
        justify-content: center; 
        
        gap: 0.5rem
    }

    
    @media (prefers-color-scheme: dark) {
        a:visited {
            /* color: #7bbdff; */
            color: rgb(100, 150, 255)

        }
    }

    
    main {
        margin-inline: auto;
        max-width: 60rem;

        /* padding-inline: 2rem; */

        font-size: 2rem;
        font-family: sans-serif;
    }



    :global(html) {
        color-scheme: light dark;
    }
</style>
