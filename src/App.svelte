<script>
  import Navbar from './components/Navbar/Navbar.svelte'
  import Main from './components/Main/index.svelte'
  import Container from './components/Container/Container.svelte'
  import Input from './components/Input/Input.svelte'
</script>

<style>
  main {
    width: 100%;
    height: 100%;
  }
</style>

<main>
  <Navbar />
  <Container>
    <Input />
    <Main />
  </Container>
</main>
