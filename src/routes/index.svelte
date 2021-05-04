<script context="module">
  import { GraphQLClient } from 'graphql-request'

  export async function load() {
    const graphcms = new GraphQLClient(
      'https://api-eu-central-1.graphcms.com/v2/cko631eevhvbw01xtdirc6jxa/master',
      {
        headers: {},
      }
    )

    const { posts } = await graphcms.request(
      `{
          posts {
            slug
            title
          }
      }`
    )

    return {
      props: {
        posts,
      },
    }
  }
</script>

<script>
  export let posts
</script>

<h1>GraphCMS blog-starter</h1>
<ul>
  {#each posts as post}
    <li>
      <a href="/blog/{post.slug}">
        {post.title}
      </a>
    </li>
  {/each}
</ul>
