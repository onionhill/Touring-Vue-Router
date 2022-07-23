<template>
  <p>Edit the event here</p>
</template>

<script>
export default {
  props: ['event'],
  data: function() {
    return {
      unsavedChanges: true
    }
  },
  beforeRouteLeave(to, from, next) {
    console.log('navgive..', this.unsavedChanges);
    if (this.unsavedChanges) {
      const answer = window.confirm(
        'Do you really want to leave? You have unsaved changes!'
      )

      if (answer) {
        next()
      } else {
        next(false)
      }
    } else {
      next()
    }
  }
}
</script>
