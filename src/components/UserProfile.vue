<template>
  <div class = "user-profile">
    <div class = "user-profile_panel">
      <h1 class = "user-profile_username">@{{ user.username }}</h1>
      <div class="user-profile_admin" v-if="user.isAdmin">Admin</div>
      <div class = "user-profile_follower-counter">
        <strong>Followers:</strong> {{ followers }}
      </div>
      <!-- <button @click="followUser">
        Follow
      </button> -->
    </div>
    <div class = "user-profile_records-wrapper">
        <Record v-for="record in user.records" :key="record.id" :username="user.username" :record="record"/>
        <!-- <div class = "user-prodile_records" v-for="record in user.records" :key="record.id">
            {{record.content}}
        </div> -->
        <!-- <div class = "user-prodile_records" v-for="(record, index) in user.records" :key="index">
            {{record.content}}
        </div> -->
    </div>
  </div>
</template>

<script>

import Record from "./Record";

export default {
  name: 'UserProfile',
  components: { Record },
  data() {
    return {
      followers: 0,
      user: {
        id: 1,
        username: 'EdwardNot',
        firstName: 'Edward',
        lastName: 'Not',
        email: 'leonardovan@yandex.ru',
        isAdmin: true,
        records: [
            {id: 1, content: "First record"},
            {id: 2, content: "Second record"}
        ]
      }
    }
  },
  watch: {
    followers(newFollowerCount, oldFollowerCount) {
      if (oldFollowerCount < newFollowerCount) {
        console.log(`${this.user.username} has gained a follower!`)
      }
    }
  },
  computed: {
    fullName() {
      return `${this.user.firstName} ${this.user.lastName}`
    }
  },
  methods: {
    followUser() {
      this.followers++
    }
  },
  mounted() {
    this.followUser()
  }
}
</script>

<style>

.user-profile {
  display: grid;
  grid-template-columns: 1fr 3fr;
  width: 100%;
  padding: 50px 5%;
}

.user-profile_panel{
  display: flex;
  flex-direction: column;
  margin-right: 50px;
  padding: 20px;
  background-color: white;
  border-radius: 5px;
  border: 1px solid #DFE3E8
}

.user-profile_admin{
    background: rebeccapurple;
    color: white;
    border-radius: 5px;
    margin-right: auto;
    padding: 0 10px;
    font-weight: bold;
}

h1{
  margin: 0;
}

</style>