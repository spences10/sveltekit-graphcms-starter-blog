<script context="module">
  import { gql, GraphQLClient } from 'graphql-request'

  export async function load(context) {
    const graphcms = new GraphQLClient(
      import.meta.env.VITE_GRAPHCMS_URL,
      {
        headers: {},
      }
    )

    const query = gql`
      query PostPageQuery($slug: String!) {
        post(where: { slug: $slug }) {
          title
          date
          content {
            html
          }
          tags
          author {
            name
            title
            picture {
              fileName
              url
            }
          }
          coverImage {
            fileName
            url
          }
        }
      }
    `

    const variables = {
      slug: context.params.slug,
    }

    const { post } = await graphcms.request(query, variables)

    return {
      props: {
        post,
      },
    }
  }
</script>

<script>
  export let post
</script>

<svelte:head>
  <title>{post.title}</title>
</svelte:head>

<h1 class="text-4xl font-semibold mb-7 text-gray-700">
  {post.title}
</h1>
<a href="/" class="inline-flex items-center mb-6">
  <img
    alt={post.author.picture.fileName}
    src={post.author.picture.url}
    class="w-12 h-12 rounded-full flex-shrink-0 object-cover object-center"
  />
  <span class="flex-grow flex flex-col pl-4">
    <span class="title-font font-medium text-gray-900"
      >{post.author.name}</span
    >
    <span class="text-gray-400 text-xs tracking-widest mt-0.5"
      >{post.author.title}</span
    >
  </span>
</a>
<div class="mb-6 flex justify-between">
  <div>
    {#if post.tags}
      {#each post.tags as tag}
        <span
          class="py-1 px-2 mr-2 rounded bg-indigo-50 text-indigo-500 text-xs font-medium tracking-widest"
          >{tag}</span
        >
      {/each}
    {/if}
  </div>
  <p class="text-gray-400 text-xs tracking-widest mt-0.5">
    {new Date(post.date).toDateString()}
  </p>
</div>
<article class="prose-xl">{@html post.content.html}</article>
