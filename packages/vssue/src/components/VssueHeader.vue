<template>
  <div class="vssue-header">
    <!-- comments-count - link to issue -->
    <a
      class="vssue-header-comments-count"
      :href="vssue.issue ? vssue.issue.link : null"
      target="_blank"
      rel="noopener noreferrer"
    >
      <span>
        {{
          vssue.comments
            ? vssue.$tc('comments', vssue.comments.count, {
                count: vssue.comments.count,
              })
            : vssue.$tc('comments', 0)
        }}
      </span>
    </a>

    <!-- powered-by - platform and vssue -->
    <span class="vssue-header-powered-by">
      <span>Powered by</span>

      <span v-if="vssue.API">
        <a
          :href="vssue.API.platform.link"
          :title="
            `${vssue.API.platform.name} API ${vssue.API.platform.version}`
          "
          target="_blank"
          rel="noopener noreferrer"
        >
          {{ vssue.API.platform.name }}
        </a>

        <span>&</span>
      </span>

      <a
        href="https://github.com/meteorlxy/vssue"
        :title="`Vssue v${vssue.version}`"
        target="_blank"
        rel="noopener noreferrer"
      >
        Vssue
      </a>
    </span>
  </div>
</template>

<script lang="ts">
import { Vue, Component, Inject } from 'vue-property-decorator';
import { Vssue } from 'vssue';

@Component
export default class VssueHeader extends Vue {
  @Inject() vssue!: Vssue.Store;
}
</script>
