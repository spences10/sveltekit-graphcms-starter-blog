<script context="module">
  import { GraphQLClient } from 'graphql-request'

  export async function load(ctx) {
    const graphcms = new GraphQLClient(
      'https://api-eu-central-1.graphcms.com/v2/cko631eevhvbw01xtdirc6jxa/master',
      {
        headers: {},
      }
    )

    const { post } = await graphcms.request(
      `query BlogPageQuery($slug :String!) {
				post(where: { slug: $slug }) {
					title
					content{
						html
					}
				}
			}`,
      {
        slug: ctx.page.params.slug,
      }
    )

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

<h1>{post.title}</h1>
{@html post.content.html}
