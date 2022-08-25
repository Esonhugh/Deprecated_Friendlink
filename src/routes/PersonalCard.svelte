<script>
    export let PersonalData = {};
    import {Card, Avatar} from '@brainandbones/skeleton';

    function JumpTo(url) {
        window.open(url, "_blank")
    }
</script>

<Card background="bg-primary-500" class="grid md:grid-cols-2 gap-3"
      color="text-white"
>
    <div class="content-center"
         on:click={()=>JumpTo(PersonalData.url)}
    >
        <Avatar alt="{PersonalData.alias}"
                background="bg-surface-500"
                hover={false} initials="PL"
                outlined={true} size="xl"
                src="{PersonalData.avatar}"
        />
        <p class="text-white p-1 text-center"
        >
            {PersonalData.alias}
        </p>
    </div>
    <div class="content-center"
         on:click={()=>JumpTo(PersonalData.url)}
    >
        <p class="text-blue-900 text-center">{PersonalData.remark}</p>
    </div>
</Card>

