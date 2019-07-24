<template lang="html">

  <div class="article">
    <a :href="article.url">
      <p id="date">{{this.getDateTime(article.datetime)}} | {{article.source}}</p>
      <p id="headline">{{article.headline}}</p>
      <p id="summary">{{article.summary}}</p>
    </a>

    <hr>

  </div>

</template>

<script>
export default {
  data(){
    return{
      formatDate: ''
    }
  },
  props: ["article"],
  methods:{
    getDateTime(timestamp){
      const months = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
      const dateTime = new Date(timestamp);
      const date = dateTime.getDate();
      const month = months[dateTime.getMonth()];
      const year = dateTime.getFullYear();
      const hours = dateTime.getHours();
      const minutes = dateTime.getMinutes();
      const formattedDateTime = date + ' ' + month + ' ' + year + ' ' + hours + ':' + minutes;
      return formattedDateTime
    }

  }
}
</script>

<style lang="css" scoped>

#date{
  font-size: 12px;
}

#headline {
  font-weight: bold;
  font-size: 26px;
}

p {
  color: black;
}

a {
  text-decoration: none;
}

.article {
  margin-left: 20px;
}

.article:hover {
  background-color: #D7D9D8;
  color: #FF6A00;
}

.article:hover p {
  color: #FF6A00;
}

</style>
