<template>
  <base-side-page
    @cancel="cancelSidePage"
    title="标签"
    icon="res-tag"
    :res-name="data.name"
    :actions="params.actions"
    :current-tab="params.windowData.currentTab"
    :tabs="detailTabs"
    @tab-change="handleTabChange">
    <component
      :is="params.windowData.currentTab"
      :res-id="params.resId"
      :data="data"
      @tab-change="handleTabChange" />
  </base-side-page>
</template>

<script>
import TagDetail from './Detail'
import BindResource from './BindResource'
import SidePageMixin from '@/mixins/sidePage'
import WindowsMixin from '@/mixins/windows'

export default {
  name: 'TagSidePage',
  components: {
    TagDetail,
    BindResource,
  },
  mixins: [SidePageMixin, WindowsMixin],
  data () {
    return {
      detailTabs: [
        { label: '详情', key: 'tag-detail' },
        { label: '绑定资源', key: 'bind-resource' },
      ],
    }
  },
  computed: {
    data () {
      return this.params.data
    },
  },
}
</script>
