<template>
  <Layout>
    <div class="project">
      <div class="container">
        <div class="project-header">
          <h1 class="project-title" v-html="$page.event.eventName"/>
          <div class="project-info">
            <div class="year-container">
              <span class="label">Start Time</span>
              <div v-html="$page.event.startTime"/>
            </div>
            <div class="year-container">
              <span class="label">End Time</span>
              <div v-html="$page.event.endTime"/>
            </div>
          </div>
        </div>

        <div v-html="$page.event.description" class="content"/>
      </div>
    </div>
  </Layout>
</template>

<page-query>
query Event ($path: String!) {
  event: event (path: $path) {
    eventName
    description
    startTime
    endTime
  }
}
</page-query>

<script>
export default {
  metaInfo() {
    return {
      title: this.$page.event.eventName
    };
  }
};
</script>

<style scoped>
.project-header {
  padding: 20vh 0 4rem 0;
}
.project-title {
  font-size: 4rem;
  margin: 0 0 4rem 0;
  padding: 0;
}
.project-info {
  display: flex;
  flex-wrap: wrap;
  font-size: 0.8rem;
}
.project-info > div {
  margin-right: 4rem;
}
.project-info > div:last-of-type {
  margin: 0;
}
.category:after {
  content: ", ";
}
.category:last-of-type:after {
  content: "";
}
</style>
