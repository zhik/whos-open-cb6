<script>
    import {formatPhoneNumber, getValidUrl} from '../../../utils/textFormatting'
    import MaterialIcon from '../../MaterialIcon.svelte'

    export let text = ''
    export let url = ''
    export let icon = 'indeterminate_check_box'
    export let type = 'text'


</script>

{#if url.trim() || text.trim()}
    {#if type === 'email'}
        <a href="mailto:{text}">
            <p class="info">
                <MaterialIcon icon={icon} alt="Email Address"/>{text}
            </p>
        </a>
    {:else if type === 'phone'}
        <a href="tel:{formatPhoneNumber(text)}">
            <p class="info">
                <MaterialIcon icon={icon} alt="Phone Number"/>{text}
            </p>
        </a>
    {:else if type === 'website' && url.trim()}
        <a target="_blank" href="{getValidUrl(url)}">
            <p class="info">
                <MaterialIcon icon={icon} alt="Website"/>{text}
            </p>
        </a>
    {:else if text !== 'Website/Instagram'}
        <p class="info">
            <MaterialIcon icon={icon}/>{text}
        </p>
    {/if}
{/if}

<style>
    .info {
        display: flex;
        align-items: center;
        font-size: 0.9rem;
        margin-bottom: 5px;
    }

    .info span {
        margin-right: 10px;
    }
</style>
