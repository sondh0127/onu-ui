<script setup lang="ts">
import { OMessage } from 'onu-ui'

function handleToClickTheme(type:String) {
  OMessage[type]({
    content: type,
  })
}

function handleBasicClick(content:string | number) {
  OMessage.primary({
    content,
  })
}
function handleCloseClick(content:string | number) {
  OMessage.info({
    content,
    closable: true,
  })
}

function handleIconClick() {
  OMessage.secondary({
    content: 'icon message',
    closable: true,
    icon: 'i-carbon-asleep',
  })
}
function handleDurationClick() {
  OMessage.error({
    content: 'duration message',
    closable: true,
    duration: 10000,
  })
}
</script>

<template>
  <o-card title="Message" o="white">
    <div space-y-2>
      <div fsc gap-2 flex-wrap>
        <o-button o="primary" @click="handleToClickTheme('primary')">
          primary message
        </o-button>
        <o-button o="secondary" @click="handleToClickTheme('secondary')">
          secondary message
        </o-button>
        <o-button o="info" @click="handleToClickTheme('info')">
          info message
        </o-button>
        <o-button o="success" @click="handleToClickTheme('success')">
          success message
        </o-button>
        <o-button o="warning" @click="handleToClickTheme('warning')">
          warning message
        </o-button>
        <o-button o="error" @click="handleToClickTheme('error')">
          error message
        </o-button>
      </div>
      <div fsc gap-2 flex-wrap>
        <o-button o="primary" @click="handleBasicClick('basic message')">
          show basic message
        </o-button>
        <o-button o="info" @click="handleCloseClick('closable message')">
          show closable message
        </o-button>
        <o-button o="secondary" @click="handleIconClick">
          icon content
        </o-button>
        <o-button o="error" @click="handleDurationClick">
          duration
        </o-button>
      </div>
    </div>
  </o-card>
</template>
