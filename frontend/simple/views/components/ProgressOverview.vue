<template>
  <div>
    <div class="level">
      <dl class="level-left c-summary" :style="{ color: fakeStore.themeColor }">
        <dt class="subtitle c-summary-key">
          <i18n>Contributed</i18n>
        </dt>
        <dd class="c-summary-value c-metric-primaryText">
          {{fakeStore.contributedFormatted}}
        </dd>
        <dt class="subtitle c-summary-key">
          <i18n>Pledged</i18n>
        </dt>
        <dd class="c-summary-value c-metric-secondaryText">
          {{fakeStore.pledgedFormatted}}
        </dd>
        <dt class="subtitle c-summary-key">
          <i18n>Goal</i18n>
        </dt>
        <dd class="c-summary-value">
          {{fakeStore.goalFormatted}}
        </dd>
      </dl>
    </div>
    <div class="c-bar" :style="{ backgroundColor: fakeStore.themeColor }">
        <span class="c-bar-progress c-metric-secondary" :style="{ width: barPercentage.pledged }"></span>
        <span class="c-bar-progress c-metric-primary" :style="{ width: barPercentage.contributed }"></span>
    </div>
  </div>
</template>

<style lang="scss" scoped>
  .c-summary {
    display: flex;
    flex-direction: column;
    flex-wrap: wrap;
    align-items: flex-start;
    max-height: 3rem;
    margin-top: 0.5rem;

    &-key {
      min-width: 7.5rem;
      margin-right: 1rem;
    }

    &-value {
      font-size: 1.7rem;
      line-height: 1;
      font-weight: 600;
      color: #616161;
    }
  }

  .c-bar {
    position: relative;
    overflow: hidden;
    width: 100%;
    height: 2.2rem;

    &::before,
    &-progress {
      position: absolute;
      display: block;
      top: 0;
      left: 0;
      height: 100%;
      background-color: inherit;
    }

    &::before {
      content: "";
      width: 100%;
      opacity: 0.8;
      background-color: #fff;
    }
  }

  .c-metric-primary {
    opacity: 0.8;

    &Text {
      color: inherit;
      opacity: 1;
    }
  }

  .c-metric-secondary {
    opacity: 0.5;

    &Text {
      color: inherit;
      opacity: 0.8;
    }
  }
</style>
<script>
export default {
  name: 'ProgressOverview',
  data () {
    return {
      fakeStore: {
        period: 'July',
        themeColor: '#5dc8f0', // The layout palette will adjust
        contributed: 350,
        pledged: 800,
        goal: 1000,
        contributedFormatted: '$350',
        pledgedFormatted: '$800',
        goalFormatted: '$1,000'
      }
    }
  },
  computed: {
    barPercentage: function () {
      return {
        pledged: `${Math.floor(this.fakeStore.pledged * 100 / this.fakeStore.goal)}%`,
        contributed: `${Math.floor(this.fakeStore.contributed * 100 / this.fakeStore.goal)}%`
      }
    }
  }
}
</script>
