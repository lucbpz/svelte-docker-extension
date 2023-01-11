<script lang="ts">
  import Header from "./lib/Header.svelte";
  import { createDockerDesktopClient } from "@docker/extension-api-client";
  const ddClient = createDockerDesktopClient();
  let response: string = "";

  const fetchAndDisplayResponse = async () => {
    response = "Loading...";
    const result = await ddClient.extension.vm?.service?.get("/hello");
    response = JSON.stringify(result);
  };
</script>

<main>
  <Header />
  <p class="description">
    This is a basic page rendered with Svelte, using some variables within
    Docker's theme. Read the Docker Extension documentation to learn more.
  </p>

  <p class="dark-mode">
    ✨ This text will change to a different color ONLY when light mode
  </p>

  <p>
    Pressing the below button will trigger a request to the backend. Its
    response will appear in the textarea.
  </p>
  <button class="primary" on:click={fetchAndDisplayResponse}
    >Call backend</button
  >
  <p class="code">{response}</p>
</main>

<style>
  .description {
    display: block;
    margin-top: 24px;
    padding-top: var(--dd-spacing-unit);
  }

  @media (prefers-color-scheme: light) {
    .dark-mode {
      color: blueviolet;
    }
  }
</style>
