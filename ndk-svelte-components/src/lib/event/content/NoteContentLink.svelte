<script lang="ts">
    // eslint-disable-next-line @typescript-eslint/no-explicit-any
    export let value: any;
    export let showMedia = false;

    const isImage = value.url.match(/^.*\.(jpg|jpeg|png|webp|gif|avif|svg)/gi);
    const isVideo = value.url.match(/^.*\.(mov|mkv|avi|m4v|webm)/gi);
    const isAudio = value.url.match(/^.*\.(ogg|mp3|wav)/gi);
</script>

{#if showMedia && value.isMedia}
    {#if isImage}
        <img src={value.url} alt={value.url} />
    {:else if isVideo}
        <!-- svelte-ignore a11y-media-has-caption -->
        <video src={value.url} controls />
    {:else if isAudio}
        <audio src={value.url} controls>
            <a href={value.url}>{value.url.replace(/https?:\/\/(www\.)?/, "")}</a>
        </audio>
    {:else}
        <a href={value.url}>
            {value.url.replace(/https?:\/\/(www\.)?/, "")}
        </a>
    {/if}
{:else}
    <a href={value.url}>
        {value.url.replace(/https?:\/\/(www\.)?/, "")}
    </a>
{/if}
