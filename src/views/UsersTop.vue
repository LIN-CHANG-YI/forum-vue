<template>
  <div class="container py-5">
    <NavTabs />
    <h1 class="mt-5">美食達人</h1>
    <hr />
    <div class="row text-center">
      <div class="col-3" v-for="user in users" :key="user.id">
        <a href="#">
          <img :src="user.image" width="140px" height="140px" />
        </a>
        <h2>{{ user.name }}</h2>
        <span class="badge badge-secondary"
          >追蹤人數：{{ user.FollowerCount }}</span
        >
        <p class="mt-3">
          <button
            v-if="user.isFollowed"
            @click.stop.prevent="deleteFollow"
            type="button"
            class="btn btn-danger"
          >
            取消追蹤
          </button>
          <button
            v-else
            @click.stop.prevent="addFollow"
            type="button"
            class="btn btn-primary"
          >
            追蹤
          </button>
        </p>
      </div>
    </div>
  </div>
</template>

<script>
import NavTabs from "../components/NavTabs.vue";

const dummyData = {
  users: [
    {
      id: 2,
      name: "user1",
      email: "user1@example.com",
      password: "$2a$10$NjMx.K9UlVkNu07QPihMF.yexZ9YtE5CTgMxMvPp7f/ILW0vnmHeC",
      isAdmin: false,
      image: "https://i.imgur.com/EQbI72p.png",
      createdAt: "2020-09-28T16:35:57.000Z",
      updatedAt: "2020-10-13T07:37:34.000Z",
      Followers: [
        {
          id: 2,
          name: "user1",
          email: "user1@example.com",
          password:
            "$2a$10$NjMx.K9UlVkNu07QPihMF.yexZ9YtE5CTgMxMvPp7f/ILW0vnmHeC",
          isAdmin: false,
          image: "https://i.imgur.com/EQbI72p.png",
          createdAt: "2020-09-28T16:35:57.000Z",
          updatedAt: "2020-10-13T07:37:34.000Z",
          Followship: {
            followerId: 2,
            followingId: 2,
            createdAt: "2020-03-25T07:52:27.000Z",
            updatedAt: "2020-03-25T07:52:27.000Z",
          },
        },
      ],
      FollowerCount: 1,
      isFollowed: true,
    },
    {
      id: 1,
      name: "root",
      email: "root@example.com",
      password: "$2a$10$qdSZAWecQ9QFoExm1lQVre3qSVcYARUGhX6L6Nu8KxYyycAX/ul4y",
      isAdmin: true,
      image: null,
      createdAt: "2020-09-28T16:35:57.000Z",
      updatedAt: "2020-10-06T03:08:56.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 3,
      name: "user2",
      email: "user2@example.com",
      password: "$2a$10$MRbzisN/Uub1Bh35xLFt7exe14I9DF974PQXbbdbi8JR768L2hj6.",
      isAdmin: false,
      image: null,
      createdAt: "2020-09-28T16:35:57.000Z",
      updatedAt: "2020-10-06T03:08:44.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
    {
      id: 882,
      name: "qkdn",
      email: "126354@qq.com",
      password: "$2a$10$z8BNeQfFUtMDPtQrfItTmueeR/rvzldkeMaoPWo2BOtxecp.1D.cW",
      isAdmin: false,
      image: null,
      createdAt: "2020-10-22T06:29:01.000Z",
      updatedAt: "2020-10-22T06:29:01.000Z",
      Followers: [],
      FollowerCount: 0,
      isFollowed: false,
    },
  ],
};

export default {
  components: {
    NavTabs,
  },
  methods: {
    fetchUser() {
      this.users = dummyData.users;
    },
    addFollow() {
      this.users = {
        ...this.users,
        isFollowed: true,
      };
    },
    deleteFollow() {
      this.users = {
        ...this.users,
        isFollowed: false,
      };
    },
  },
  data() {
    return {
      users: [],
    };
  },
  created() {
    this.fetchUser();
  },
};
</script>>