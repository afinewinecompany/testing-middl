<template>
  <div class="create-post">
    <form @submit.prevent="submitPost">
      <label for="post-title">Title:</label>
      <input type="text" id="post-title" v-model="title" required>

      <label for="post-body">Body:</label>
      <textarea id="post-body" v-model="body" required></textarea>

      <button type="submit">Post</button>
    </form>
  </div>
</template>

<script>
export default {
  data() {
    return {
      title: '',
      body: ''
    }
  },
  methods: {
    submitPost() {
      // send post data to server
      axios.post('/api/posts', {
        title: this.title,
        body: this.body
      })
      .then(response => {
        // handle success
        console.log(response.data)
      })
      .catch(error => {
        // handle error
        console.error(error)
      })

      // clear form fields
      this.title = ''
      this.body = ''
    }
  }
}
</script>
