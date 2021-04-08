<script context="module">
  import Client from './../../utils/client';
  import PrismicDom from 'prismic-dom';

  export async function load() {
    const document = await Client.getByUID('page', 'homepage');
    return {
      props: {
        document,
      },
    };
  }
</script>

<script>
  import './../styles/reset.css';
  import './../styles/globals.css';
  export let document;
</script>

<main>
  <div
    class="header container"
    style="background-image: url('{document.data.image.url}')"
  >
    <h1>
      {document.data.title}
    </h1>
  </div>
  <div class="container">
    <div class="text">
      {@html PrismicDom.RichText.asHtml(document.data.content)}
    </div>
  </div>
</main>

<style>
  main {
    font-family: sans-serif;
  }

  .container {
    display: flex;
    flex-direction: column;
    align-items: center;
    padding: 0px 20px;
  }

  .container > * {
    width: 100%;
    max-width: 700px;
  }

  .header {
    color: white;
    background-size: cover;
    min-height: 25vw;
    padding-top: 2rem;
    justify-content: flex-end;
  }
</style>
