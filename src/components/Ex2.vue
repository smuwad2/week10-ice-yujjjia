<script>
    // Import BlogPost component
    import blogPost from './subcomponents/BlogPost.vue'
    import axios from 'axios'
    export default {
        components: {
            blogPost
        },
        data() {
            return {
                posts: [], // array of post objects
                loading: true
            }  
        },
        computed: {
            baseUrl() {
                // Always use localhost:3000 in all environments
                return 'http://localhost:3000'
            }
        },
        async created() {
            const url = `${this.baseUrl}/posts`
            console.log('Requesting API URL:', url)

            try {
                // Add a small delay to ensure backend is ready in test environment
                await new Promise(resolve => setTimeout(resolve, 100))
                
                const response = await axios.get(url, { 
                    timeout: 10000,
                    headers: {
                        'Accept': 'application/json'
                    }
                })
                this.posts = response.data
                this.loading = false
                console.log('Posts loaded:', response.data)
            } catch (error) {
                console.error('Axios error:', error)
                this.loading = false
                if (!error.response) {
                    this.posts = [{ entry: `Network error — can't reach API at ${url} (is backend running?)` }]
                } else {
                    this.posts = [{ entry: `There was an error: ${error.message}` }]
                }
            }
        }
    }
</script>

<template>
   <!-- TODO: make use of the 'blog-post' component to display the blog posts -->
    <div>
        <blog-post v-for="post in posts" :subject="post.subject" 
        :entry="post.entry" :mood="post.mood" :key="post.id"></blog-post>
    </div>

</template>