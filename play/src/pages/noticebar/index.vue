<template>
  <view class="demo full">
    <view class="h2">{{ translate('basic') }}</view>
    <vin-noticebar :text="translate('text')"></vin-noticebar>

    <view class="h2">{{ translate('scrollable') }}</view>
    <vin-noticebar
      :text="translate('textShort')"
      :scrollable="true"
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
    >
    </vin-noticebar>
    <view style="display: block"></view>
    <vin-noticebar
      :text="translate('text')"
      :scrollable="false"
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
    ></vin-noticebar>

    <view class="h2">{{ translate('mode') }}</view>
    <vin-noticebar
      :closeMode="true"
      @click="hello"
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
      >{{ translate('text') }}
    </vin-noticebar>
    <view style="display: block"></view>
    <vin-noticebar
      :closeMode="true"
      right-icon="circle-close"
      @click="hello"
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
      >{{ translate('text') }}
    </vin-noticebar>
    <view style="display: block"></view>
    <vin-noticebar
      left-icon="https://img13.360buyimg.com/imagetools/jfs/t1/72082/2/3006/1197/5d130c8dE1c71bcd6/e48a3b60804c9775.png"
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
    >
      <a href="http://vingogo.cn/docs/index.html">{{ translate('vin') }}</a>
    </vin-noticebar>

    <view class="h2">{{ translate('multiline') }}</view>
    <vin-noticebar
      :text="translate('text')"
      wrapable
      :background="`rgba(251, 248, 220, 1)`"
      :color="`#D9500B`"
    ></vin-noticebar>

    <view class="h2">{{ translate('vertical') }}</view>
    <view class="interstroll-list">
      <vin-noticebar
        direction="vertical"
        :list="horseLamp1"
        :speed="10"
        :standTime="1000"
        @click="go"
        :closeMode="true"
        :background="`rgba(251, 248, 220, 1)`"
        :color="`#D9500B`"
      ></vin-noticebar>
    </view>

    <view class="h2">{{ translate('complexAm') }}</view>
    <view class="interstroll-list">
      <vin-noticebar
        direction="vertical"
        :list="horseLamp2"
        :speed="10"
        :standTime="2000"
        :complexAm="true"
        :background="`rgba(251, 248, 220, 1)`"
        :color="`#D9500B`"
      ></vin-noticebar>
    </view>
    <!-- uniapp 限制，暂不支持 -->
    <!-- <view class="h2">{{ translate('customAm') }}</view>
    <view class="interstroll-list">
      <vin-noticebar
        direction="vertical"
        :height="50"
        :speed="10"
        :standTime="1000"
        :list="[]"
        @close="go"
        :background="`rgba(251, 248, 220, 1)`"
        :color="`#D9500B`"
      >
        <view
          class="custom-item"
          :data-index="index"
          v-for="(item, index) in horseLamp3"
          style="height: 50px; line-height: 50px"
          :key="index"
        >
          {{ item }}
        </view>
      </vin-noticebar>
    </view> -->

    <view class="h2">{{ translate('customRightIcon') }}</view>
    <view class="interstroll-list">
      <vin-noticebar
        direction="vertical"
        :list="horseLamp1"
        :speed="10"
        :standTime="1000"
        :background="`rgba(251, 248, 220, 1)`"
        :color="`#D9500B`"
      >
        <template v-slot:rightIcon>
          <vin-icon name="fabulous" color="#f0250f"> </vin-icon>
        </template>
      </vin-noticebar>
    </view>
  </view>
</template>

<script lang="ts">
import { onMounted, reactive, toRefs } from 'vue';
import { createComponent } from '@vingogo/uni-ui/common/create';
import { useTranslate } from '@/hooks/useTranslate';

const { createDemo, translate } = createComponent('noticebar');

useTranslate({
  'zh-CN': {
    basic: '基础使用',
    scrollable: '滚动播放',
    mode: '通告栏--关闭模式',
    multiline: '多行展示',
    vertical: '垂直滚动',
    complexAm: '纵向--复杂滚动动画',
    customAm: '纵向--自定义滚动内容',
    customRightIcon: '纵向--自定义右侧图标',
    text: 'VinUI 使用 Vue 语言来编写可以在 H5，小程序平台上的应用，帮助研发人员提升开发效率，改善开发体验。',
    textShort: 'VinUI 是移动端组件库',
    horseLamp: [
      'NoticeBar 公告栏',
      'Cascader 级联选择',
      'DatePicker 日期选择器',
      'CheckBox 复选按钮',
    ],
    vin: 'Vin',
  },
  'en-US': {
    basic: 'Basic Usage',
    scrollable: 'Scrollable',
    mode: 'Mode',
    multiline: 'Wrapable',
    vertical: 'Vertical Scroll',
    complexAm: 'Vertical Scroll Complex Animation',
    customAm: 'Vertical Scroll Custom Style',
    customRightIcon: 'Vertical Scroll Custom Right Icon',
    text: 'VinUI uses Vue language to write applications that can be used on H5 and applet platforms to help R & D personnel improve development efficiency and development experience.',
    textShort: 'VinUI is a mobile terminal component library.',
    horseLamp: ['NoticeBar', 'Cascader', 'DatePicker', 'CheckBox'],
    vin: 'Vin',
  },
});

export default createDemo({
  props: {},
  setup() {
    const state = reactive({
      horseLamp1: translate('horseLamp'),
      horseLamp2: translate('horseLamp'),
      horseLamp3: translate('horseLamp'),
      text: translate('text'),
    });

    const hello = () => {
      console.log('hello world');
    };
    const go = (item: any) => {
      console.log(item);
    };

    return {
      ...toRefs(state),
      hello,
      go,
      translate,
    };
  },
});
</script>

<style lang="scss" scoped>
.demo {
  padding-bottom: 30px !important;

  // .interstroll-list {
  //   padding: 0 10px;
  //   background: rgba(251, 248, 220, 1);
  //   color: #d9500b;
  // }
}
</style>
