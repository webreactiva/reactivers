<template>
  <div class="flex-1 flex-wrap bg-gradient-t-black-900-300">
    <div class="m-4 mb-0">
      <category-filters
        :categories="mainSkills"
        @change="selectMainSkills = $event"
      ></category-filters>
      <category-filters
        :categories="skills"
        @change="selectSkills = $event"
      ></category-filters>
    </div>

    <div class="md:flex md:flex-wrap p-2">
      <profile-item
        v-for="(profile, index) in activeProfiles"
        :key="index"
        :profile="profile"
      ></profile-item>
    </div>
  </div>
</template>

<script>
import profiles from "~/static/profiles.json";
import ProfileItem from "~/components/ProfileItem.vue";
import CategoryFilters from "~/components/CategoryFilters.vue";

export default {
  components: {
    ProfileItem,
    CategoryFilters,
  },
  data() {
    return {
      selectSkills: [],
      selectMainSkills: [],
      skills: [],
      mainSkills: [],
      profiles,
    };
  },
  computed: {
    activeProfiles: function() {
      if (this.selectSkills.length == 0 && this.selectMainSkills.length == 0) {
        return this.profiles;
      }

      return this.profiles.filter((profile) => {
        return (
          this.selectMainSkills.some(
            (choice) => profile.main_skill.indexOf(choice) != -1
          ) &&
          this.selectSkills.every(
            (choice) => profile.skills.indexOf(choice) != -1
          )
        );
      });
    },
  },
  mounted() {
    this.getSkills();
    this.getMainSkills();
  },
  methods: {
    getSkills() {
      profiles.map((item) => {
        item.skills.map((skill) => {
          if (!this.checkIfExists(skill, this.skills)) {
            this.skills.push(skill);
          }
        });
      });
    },
    getMainSkills() {
      profiles.map((profile) => {
        if (!this.checkIfExists(profile.main_skill, this.mainSkills)) {
          this.mainSkills.push(profile.main_skill);
        }
      });
    },
    checkIfExists(search, items) {
      return items.some((item) => item === search);
    },
  },
};
</script>
