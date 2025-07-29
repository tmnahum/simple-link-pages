<script>
  import { invalidateAll } from "$app/navigation";
    import CreateYourOwn from "./CreateYourOwn.svelte";

    export let data;

</script>

<!-- 
only in svelte 5:
{#snippet link(href, title)}
	<a href={href} data-sveltekit-reload>{title}</a>
{/snippet} 
doing this to band aid fix bug where going back from destination does not change page content
-->
<main>
    
    <h1> Simple link pages </h1>

    <p> I made this so i can favorite groups of urls in arc/zen browser in one tab.</p>
    <p>Feel free to use however you like!</p>
    <br>
    <p> Links on pages should open within the same tab in zen essentials.</p>
    <br>
    <!-- <p> 
        Custom page data is fully encoded into the url using queryParams. <br>
    </p> -->


    <p></p>

    <h2>Example Links:</h2>
    <ul style="">
        <li>
            <a href="/ai" data-sveltekit-reload>ai chat</a>,
            <a 
                href="/custom?data=%7B%22title%22%3A%22AI%20Links%22%2C%22favicon%22%3A%7B%22dark%22%3A%22%5Cn%20%20%20%20%20%20%20%20data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij48cGF0aCBmaWxsPSJub25lIiBzdHJva2U9IiNmZmYiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgc3Ryb2tlLXdpZHRoPSIxLjUiIGQ9Ik0xMiAyMS4yNWE5LjI1IDkuMjUgMCAxIDAtOC4zMDctNS4xNzdjLjEwOC4yMi4xNDQuNDY4LjA4OS43MDZsLS44MTYgMy41MzZhLjYuNiAwIDAgMCAuNzIuNzJsMy41MzUtLjgxN2ExLjA2IDEuMDYgMCAwIDEgLjcwNi4wOUE5LjIgOS4yIDAgMCAwIDEyIDIxLjI1TTcuOTcgOS44ODZoOC4wNm0tOC4wNiA0LjIyOGg1Ljc0OCIvPjwvc3ZnPg%3D%3D%5Cn%20%20%20%20%20%20%22%2C%22light%22%3A%22%5Cn%20%20%20%20%20%20%20%20data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij48cGF0aCBmaWxsPSJub25lIiBzdHJva2U9IiMwMDAiIHN0cm9rZS1saW5lY2FwPSJyb3VuZCIgc3Ryb2tlLWxpbmVqb2luPSJyb3VuZCIgc3Ryb2tlLXdpZHRoPSIxLjUiIGQ9Ik0xMiAyMS4yNWE5LjI1IDkuMjUgMCAxIDAtOC4zMDctNS4xNzdjLjEwOC4yMi4xNDQuNDY4LjA4OS43MDZsLS44MTYgMy41MzZhLjYuNiAwIDAgMCAuNzIuNzJsMy41MzUtLjgxN2ExLjA2IDEuMDYgMCAwIDEgLjcwNi4wOUE5LjIgOS4yIDAgMCAwIDEyIDIxLjI1TTcuOTcgOS44ODZoOC4wNm0tOC4wNiA0LjIyOGg1Ljc0OCIvPjwvc3ZnPg%3D%3D%5Cn%20%20%20%20%20%20%22%7D%2C%22links%22%3A%5B%7B%22href%22%3A%22https%3A%2F%2Fchatgpt.com%2F%3Ftemporary-chat%3Dtrue%22%2C%22title%22%3A%22ChatGPT%20temporary%22%2C%22faviconUrl%22%3A%22%22%7D%2C%22br%22%2C%7B%22title%22%3A%22ChatGPT%22%2C%22href%22%3A%22https%3A%2F%2Fchatgpt.com%2F%22%7D%2C%7B%22title%22%3A%22Gemini%22%2C%22href%22%3A%22https%3A%2F%2Fgemini.google.com%2Fapp%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Faistudio.google.com%2F%22%2C%22title%22%3A%22Ai%20Studio%22%2C%22faviconUrl%22%3A%22%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Fgrok.com%22%2C%22title%22%3A%22Grok%22%2C%22faviconUrl%22%3A%22%22%7D%2C%7B%22title%22%3A%22T3%20chat%22%2C%22href%22%3A%22https%3A%2F%2Ft3.chat%22%7D%2C%7B%22title%22%3A%22Claude%22%2C%22href%22%3A%22https%3A%2F%2Fwww.claude.ai%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Fpoe.com%2F%22%2C%22title%22%3A%22Poe%22%2C%22faviconUrl%22%3A%22%22%7D%2C%22br%22%5D%7D",
                data-sveltekit-reload
            >two</a>,
            <a href="/custom?data=%7B%22title%22%3A%22AI%20Links%22%2C%22favicon%22%3A%22data%3Aimage%2Fsvg%2Bxml%3Bbase64%2CPHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHdpZHRoPSIyNCIgaGVpZ2h0PSIyNCIgdmlld0JveD0iMCAwIDI0IDI0Ij48cGF0aCBmaWxsPSIjZmZmIiBkPSJtMjAuNzEzIDguMTI4bC0uMjQ2LjU2NmEuNTA2LjUwNiAwIDAgMS0uOTM0IDBsLS4yNDYtLjU2NmE0LjM2IDQuMzYgMCAwIDAtMi4yMi0yLjI1bC0uNzU5LS4zMzlhLjUzLjUzIDAgMCAxIDAtLjk2M2wuNzE3LS4zMTlhNC4zNyA0LjM3IDAgMCAwIDIuMjUxLTIuMzI2bC4yNTMtLjYxMWEuNTA2LjUwNiAwIDAgMSAuOTQyIDBsLjI1My42MWE0LjM3IDQuMzcgMCAwIDAgMi4yNSAyLjMyN2wuNzE4LjMyYS41My41MyAwIDAgMSAwIC45NjJsLS43Ni4zMzhhNC4zNiA0LjM2IDAgMCAwLTIuMjE5IDIuMjUxTTEwIDNoNHYyaC00YTYgNiAwIDAgMC02IDZjMCAzLjYxIDIuNDYyIDUuOTY2IDggOC40OFYxN2gyYTYgNiAwIDAgMCA2LTZoMmE4IDggMCAwIDEtOCA4djMuNWMtNS0yLTEyLTUtMTItMTEuNWE4IDggMCAwIDEgOC04Ii8%2BPC9zdmc%2B%22%2C%22links%22%3A%5B%7B%22title%22%3A%22T3%20Chat%22%2C%22href%22%3A%22https%3A%2F%2Ft3.chat%22%7D%2C%7B%22title%22%3A%22Claude%22%2C%22href%22%3A%22https%3A%2F%2Fwww.claude.ai%22%7D%2C%7B%22title%22%3A%22Gemini%22%2C%22href%22%3A%22https%3A%2F%2Fgemini.google.com%2Fapp%22%7D%2C%7B%22title%22%3A%22ChatGPT%22%2C%22href%22%3A%22https%3A%2F%2Fchatgpt.com%2F%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Fchatgpt.com%2F%3Ftemporary-chat%3Dtrue%22%2C%22title%22%3A%22GPT%20temporary%22%2C%22faviconUrl%22%3A%22%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Fgrok.com%22%2C%22title%22%3A%22Grok%22%2C%22faviconUrl%22%3A%22%22%7D%2C%22br%22%2C%7B%22href%22%3A%22https%3A%2F%2Fwww.google.com%2Fsearch%3Fq%3D%26sca_esv%3D5f3e024f075fa025%26hl%3Den%26source%3Dhp%26ei%3DTCCJaP2dILSf5NoP-or1mA0%26iflsig%3DAOw8s4IAAAAAaIkuXHc0L14JHbe4Dx4T5kcjl9UQyOad%26aep%3D22%26udm%3D50%26ved%3D0ahUKEwj9896I5uKOAxW0D1kFHXpFHdMQteYPCAk%22%2C%22title%22%3A%22Google%20AI%22%2C%22faviconUrl%22%3A%22%22%7D%2C%7B%22href%22%3A%22https%3A%2F%2Fwww.perplexity.ai%2F%22%2C%22title%22%3A%22Perplexity%22%2C%22faviconUrl%22%3A%22%22%7D%2C%22br%22%5D%7D">three</a>,
            <a href="/ai2" data-sveltekit-reload>long</a>
        </li>


        <li><a href="/music" data-sveltekit-reload>music</a></li>
        
        <li><a href="/messaging" data-sveltekit-reload>messaging</a></li>
        <li><a href="/notes" data-sveltekit-reload>notes apps</a></li>
    </ul>

    {#if data}
        <CreateYourOwn defaultData={data}/>
    {:else}
        <CreateYourOwn />
    {/if}
    <br>
    <!-- <p>(remove the word "custom" from a url to edit the links of that page)</p>
    <p>(or look in the browser console)</p> -->

    <br>
    <p style="margin-top: 7rem">More random tools at <a href="https://www.ttools.io" data-sveltekit-reload >ttools.io</a></p>
</main>

<svelte:head>
    <title>Simple Link Pages - create your own</title>
    <meta name="description" content="Create your own webpage of links. Great for pinned tabs or bookmarks! Can also use for sharing. In zen browser, links open inside the same tab when pinned to essentials.">
    
    <link rel="canonical" href="https://links.ttools.io">
    
</svelte:head>

<style>
    main {
        margin-inline: auto;
        max-width: 70ch;

        /* padding-inline: 2rem; */

        font-size: 1.2rem;
        font-family: sans-serif;
        
    }

    p {
        margin: .2rem 0
    }
    h2 {
        margin-bottom: .3rem;
    }
    ul {
        margin-top: 0
    }

    :global(html) {
        color-scheme: light dark;
    }

    @media (prefers-color-scheme: dark) {
        main {
            color: hsl(0, 0%, 90%);
        }
    }
</style>
