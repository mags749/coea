<script>
  import Header from "./components/Header/Header.svelte";
  import Main from "./components/Main/Main.svelte";
  import Footer from "./components/Footer/Footer.svelte";
</script>

<Header />
<Main />
<Footer />

<style global lang="postcss">
  @tailwind base;
  @tailwind components;
  @tailwind utilities;
</style>
