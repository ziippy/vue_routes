<template lang="html">
  <div>
    <h1>Contacts</h1>
    <div class="wrapper">
      <div class="box" v-for="c in contacts" :key="c.no">
        <!--
        <router-link v-bind:to="'/contacts/' + c.no">{{ c.name }}</router-link>
        -->
        <!-- 명명된 라우트
        <router-link v-bind:to="{ name:'contactbyno', params:{ no:c.no }}">{{ c.name }}</router-link>
        -->
        <span @click="navigate(c.no)" style="cursor:pointer">[ {{ c.name }} ]</span>
      </div>
    </div>
    <router-view></router-view>
  </div>
</template>

<script>
import contactlist from '../ContactList';

export default {
  name: "contacts",
  data: function() {
    return {
      contacts : contactlist.contacts
    }
  },
  methods: {
    navigate(no) {
      if (confirm('상세 정보를 보시겠습니까?')) {
        this.$router.push({ name: 'contactbyno', params : { no: no }}, function() {
          console.log('/contacts/' + no + " 로 이동 완료!")
        })
      }
    }
  }
}
</script>

<style lang="css" scoped>
  .wrapper { background-color:#FFF; clear:both; display:table; }
  .box { float:left; background-color:aqua; border-radius:5px;
          padding:10px; margin:3px; text-align:center; font-size:120%;
          width:100px; font-weight:bold; }
  a:link, a:visited { text-align:center; text-decoration:none; display:inline-block; }
</style>
