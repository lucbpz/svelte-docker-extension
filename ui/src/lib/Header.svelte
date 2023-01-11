<script lang="ts">
  import svelteLogo from "../assets/svelte.svg";
  import { createDockerDesktopClient } from "@docker/extension-api-client";
  const ddClient = createDockerDesktopClient();
  const FEEDBACK_FORM_URL = "https://docker.com";
</script>

<section>
  <div class="header">
    <a href="https://svelte.dev" target="_blank" rel="noreferrer">
      <img src={svelteLogo} class="logo svelte" alt="Svelte Logo" />
    </a>
    <h1>Docker extension demo</h1>
    <a href="#" on:click={() => ddClient.host.openExternal(FEEDBACK_FORM_URL)}
      >Give Feedback</a
    >
  </div>
</section>

<style>
  .header {
    display: flex;
    align-items: center;
    gap: var(--dd-spacing-unit);
  }
  .logo:hover {
    filter: drop-shadow(0 0 2em #646cffaa);
  }
  .logo.svelte:hover {
    filter: drop-shadow(0 0 2em #ff3e00aa);
  }
</style>
