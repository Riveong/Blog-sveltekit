<script>
	import { onMount } from 'svelte';
	export let posts = [];
    export let sub
    export let image
    export let content
  
	onMount(()=>{fetch('/posts/sample-blog.json')
    	.then(response => response.json())
    	.then(blog => {
      		posts = blog.data;

              for (const post of posts) {
                    if (post.title === data.title) {
                        sub = post.desc;
                        image = post.imageurl;
                        content = post.content;
                        
                    }
                }
    })});


    export let data;
    
</script>
<a href="/" class="btn">👈 Back to home</a>
<img src={image} class="cover">
<h1>{data.title}</h1>
<h3>{sub}</h3>
<p>{@html content}</p>

<style>

    .cover{
        width: 100%;
        max-height: 300px;
        object-fit: cover;
        
    }
    p { letter-spacing: 1px; line-height: 2}

    .btn {
        background-color: #0c0a18;
        color: white;
        padding: 5px 10px;
        text-decoration: none;
    }

</style>