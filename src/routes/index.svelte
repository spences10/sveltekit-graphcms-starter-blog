<script context="module">
  import { gql, GraphQLClient } from 'graphql-request'

  export async function load() {
    const graphcms = new GraphQLClient(
      import.meta.env.VITE_GRAPHCMS_URL,
      {
        headers: {},
      }
    )

    const query = gql`
      query PostsIndex {
        posts {
          title
          slug
          date
          excerpt
          coverImage {
            fileName
            url
          }
        }
      }
    `

    const { posts } = await graphcms.request(query)

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

<h1 class="text-4xl font-semibold mb-7 text-gray-700">
  GraphCMS starter blog
</h1>
<ul>
  <li>
    {#each posts as post}
      <div class="card text-center shadow-xl border mb-10">
        <figure class="px-10 pt-10">
          <img
            src={post.coverImage.url}
            alt={post.coverImage.fileName}
            class="rounded-xl"
          />
        </figure>
        <div class="card-body">
          <h2 class="card-title">{post.title}</h2>
          <p class="prose-lg">{post.excerpt}</p>
          <div class="justify-end card-actions">
            <a href="post/{post.slug}" class="btn btn-secondary"
              >➜ {post.title}</a
            >
          </div>
        </div>
      </div>
    {/each}
  </li>
</ul>
