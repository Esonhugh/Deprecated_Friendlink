<script>
    import PersonalCard from "./PersonalCard.svelte"

    let PersonalDataArray = [];

    async function GetPersonalDataJson() {
        const res = await fetch('friends.json')
        const text = await res.json()
        if (res.ok) {
            PersonalDataArray = text
            return text
        } else {
            throw new Error(text)
        }
    }
</script>

<h1 class="font-black text-4xl text-center text-blue-700 p-2">
    Esonhugh Blog FriendLink
</h1>
<p class="text-blue-500 text-center">
    This is Esonhugh Blog Friendlink, Visit this
    <a alt="Github" href="https://github.com/Esonhugh/Friendlink_rebuild">Github repo</a>
    to Add your Friend link with PR.
</p>
<div class="p-3">
    {#await GetPersonalDataJson()}
        <pre class="text-center p-3"> Loading..... </pre>
    {:then text}
        <div class="flex-1 gap-3 grid md:grid-cols-3 ">
            {#each PersonalDataArray as PersonalData}
                <PersonalCard {PersonalData}/>
            {/each}
        </div>
    {:catch e}
        <pre class="text-center p-3"> {e} </pre>
    {/await}
</div>

<footer class="text-center">
    Esonhugh - 2022
</footer>
