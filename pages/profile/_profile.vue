<template>
  <div>
    <h1>Your Profile</h1>
    <p>{{ firstName }}</p>
  </div>
</template>

<script> 
function getUserData () {
  const userName = 'Jam'
  return new Promise(resolve => {
    return setTimeout(() => { return resolve(userName) }, 1000)
  })
}
getUserData().then(data => console.log(data))
export default {
  async asyncData() {
    const firstName = await getUserData()
    return { firstName }
  },
  head() {
    return { title: this.firstName + ' ass' }
  }
}
</script>
