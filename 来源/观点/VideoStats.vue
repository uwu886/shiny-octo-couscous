<!-- src/components/VideoStats.vue -->
<template>
  <div class="video-stats">
    <v-chart :options="chartOptions" />
  </div>
</template>

<script>
import { ref } from 'vue';
import { use } from 'echarts/core';
import { PieChart } from 'echarts/charts';
import {
  TitleComponent,
  TooltipComponent,
  LegendComponent
} from 'echarts/components';
import VChart, { THEME_KEY } from 'vue-echarts';

// register the required components
use([TitleComponent, TooltipComponent, LegendComponent, PieChart]);

export default {
  name: 'VideoStats',
  props: {
    video: {
      type: Object,
      required: true
    }
  },
  components: {
    VChart
  },
  provide: {
    [THEME_KEY]: 'light'
  },
  setup(props) {
    const chartOptions = ref({
      title: {
        text: '视频数据',
        left: 'center'
      },
      tooltip: {
        trigger: 'item'
      },
      legend: {
        top: '5%',
        left: 'center'
      },
      series: [
        {
          name: '视频数据',
          type: 'pie',
          radius: '50%',
          data: [
            { value: props.video.views, name: '播放量' },
            { value: props.video.likes, name: '点赞数' },
            { value: props.video.comments, name: '评论数' }
          ]
        }
      ]
    });

    return { chartOptions };
  }
};
</script>

<style scoped>
.video-stats {
  width: 100%;
  height: 400px;
}
</style>

<!-- src/views/VideoDetails.vue -->
<template>
  <!-- ... -->
  <div class="video-info">
    <!-- ... -->
  </div>
  <video-comments :videoId="video.id" />
  <video-stats :video="video" />
</template>

<script>
import VideoStats from '@/components/VideoStats.vue';
// ...

export default {
  // ...
  components: {
    VideoComments,
    VideoStats
  },
  // ...
};
</script>
