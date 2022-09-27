<script>
  import { getContext } from "svelte";

  export let imageUrl;
  export let label;
  export let caption;
  export let size;
  export let details;

  const { styleable } = getContext("sdk");
  const component = getContext("component");

  console.log(component);
</script>

<div use:styleable={$component.styles}>
  <div class="container">
    <div style="flex: 0 0 auto;">
      <img
        src={imageUrl}
        alt="avatar"
        class="img-class"
        style="--size:{size}"
      />
    </div>
    {#if details}
    <div class="text-container">
      <span>{label}</span>
      <p class="caption">{caption}</p>
    </div>
    {/if}
  </div>
</div>

<style>
  .container {
    display: flex;
    align-items: center;
  }

  .img-class {
    border-radius: 50%;
    -webkit-box-flex: 0;
    -ms-flex: 0 0 auto;
    flex: 0 0 auto;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
    height: var(--size, 24px);
    overflow: hidden;
    position: relative;
    width: var(--size, 24px);
    object-fit: cover;
  }
  .text-container {
    color: black;
    font-size: 12px;
    font-weight: 600;
    -webkit-box-flex: 1;
    -ms-flex: 1 0 0px;
    flex: 1 0 0;
    line-height: 16px;
    min-width: 0;
    overflow-wrap: break-word;
    margin-left: 8px;
    text-align: left;
    max-width: 100%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
    line-height: normal;
  }

  .caption {
    font-weight: 400;
    max-width: 100%;
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  }
</style>
