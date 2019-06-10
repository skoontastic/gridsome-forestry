<template>
  <Layout>
    <div class="container">
      <Hero/>
      <ProjectsGrid :projects="$page.projects.edges"/>
    </div>
    <LatestJournals :journals="$page.journals.edges"/>
    <Events :events="$page.events.edges"/>
  </Layout>
</template>

<page-query>
query Posts {
	projects: allProjectPost {
    edges {
      node {
        id
        date (format: "D. MMMM YYYY")
        title
        categories
        thumbnail (quality: 90)
        path
      }
    }
  },
  journals: allJournalPost (perPage: 4) {
    edges {
      node {
        id
        path
        title
      }
    }
  },
  events: allEvent {
    edges {
      node {
        eventName,
        startTime,
        endTime,
        description,
        allDay,
        path
      }
    }
  }
}

</page-query>

<script>
import Hero from "@/components/Hero";
import ProjectsGrid from "@/components/ProjectsGrid";
import LatestJournals from "@/components/LatestJournals";
import Events from "@/components/Events";

export default {
  components: {
    Hero,
    ProjectsGrid,
    LatestJournals,
    Events
  }
};
</script>
