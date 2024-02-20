<script>
	import { onMount } from 'svelte';
    import Nav from './nav.svelte';
	export let posts = []; // Initialize with an empty array
  
	onMount(()=>{fetch('posts/sample-blog.json')
    	.then(response => response.json())
    	.then(data => {
      		posts = data.data;
    })});
  </script>
    <Nav/>
  <div>  
    <table>

        <tr>
            <td>
                <img src="https://avatars.githubusercontent.com/u/53504975?s=400&u=825ad6c779adb5133f6596901b4f2d6bcd836e2f&v=4" alt="a" class="profile">
            </td>
            <td>
                <h1>Riveong's Blog</h1>
            </td>
        </tr>
        
        
    </table>
    
    
    
  </div>

  <hr>
  <h3>Latest Posts</h3>

  <div class="carousel">
  {#if posts.length > 0}
    {#each posts as post}

    <div class="card">
        <img src="{post.imageurl}" alt="{post.title} pic" style="width:100%">
        <div class="container">
            <h4><b>{post.title}</b></h4>
            <p>{post.desc}</p>
            <a class="btn" href={`/blog/${post.title}`}>Read More</a>
        </div>
    </div>
  {/each}
    {:else}
    <p>No blog posts available.</p>
  {/if}
</div>

  <h3>Post Links</h3>
  <ul>
	{#if posts.length > 0}
	  {#each posts as post}
		<li>
		  <a href={`/blog/${post.title}`}>{post.title}</a>
		</li>
	  {/each}
	{:else}
	  <p>No blog posts available.</p>
	{/if}
  </ul>
  
  <style>
    h1{
        text-align: left;
    }
    .profile {
      max-width: 60px;
      border-radius : 100%;
    }
    td{padding: 10px;}

    .card-image{
        width: 100px;
    }
    .card {
        box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
        transition: 0.3s;
        border-radius: 5px; /* 5px rounded corners */
        width: 200px;
        min-width: 200px;
        margin: 20px;
    }
    .container{
        margin: 20px;
    }
    .carousel {
        display: flex;
        overflow-x: auto;
        scroll-behavior: smooth;
        -webkit-overflow-scrolling: touch;
        
    }
    .btn {
        background-color: #0c0a18;
        color: white;
        padding: 5px 10px;
        text-decoration: none;
    }

/* Add rounded corners to the top left and the top right corner of the image */
img {
  border-radius: 5px 5px 0 0;
}
  </style>