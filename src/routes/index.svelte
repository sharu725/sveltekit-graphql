<script context="module">
  import { request, gql } from "graphql-request";

  const query = gql`
    {
      countries {
        name
        emoji
      }
    }
  `;

  export const load = async () => {
    const data = await request("https://countries.trevorblades.com/", query);

    return {
      props: {
        data,
      },
    };
  };
</script>

<script>
  export let data;
</script>

<!-- {JSON.stringify(data)} -->

<h1>Countries</h1>

{#each data.countries as { name, emoji }}
  <p>{emoji} {name}</p>
{/each}
