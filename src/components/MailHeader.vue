<template>
  <div class="mail-header">
    <div class="upper">
      From: <span class="from-address">Sky</span><br>
      To: <span class="to-name">Sky Customer</span>
    </div>
    <div class="lower">
      <span class="subject">This week on Sky</span><br>
      <span class="timestamp">Today at 13:37</span>
    </div>
  </div>
</template>
<script>
export default {
  name: 'MailHeader'
}
// script to add in different to/from/subject/time data - just because
</script>
<style scoped>
  .mail-header {
    font-family: -apple-system, BlinkMacSystemFont, sans-serif;
    font-size: 12px;
    line-height: 1.5;
    text-align: left;

    padding-left: 10px;
  }
  .upper, .lower {
    border-bottom: 1px solid lightgray;
    padding: 10px 0px;
  }
  .upper {
    line-height: 2.0;
    font-weight: bold;
  }
  .upper .to-name {
    font-weight: normal;
  }
  .from-address, .to-name {
    color: #65acef;
  }
  .subject {
    font-weight: bold;
    font-size: 14px;
  }
  .timestamp {
    color: #999999;
  }
</style>
