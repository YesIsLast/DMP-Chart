<template>
  <div class="about">
    <h1>{{ leenamecom }}</h1>

    <button @click="clickBtn">调用函数</button>
  </div>
</template>
<script>
import { computed, reactive, ref, toRefs } from "vue";
export default {
  setup() {
    const dataname = "小李同学";
    const refname = ref("小小");
    const leeobj = reactive({
      leename: "小李同学leenasme",
      leenamecom: computed(() => {
        return dataname + "computed";
      }),
    });
    
    function clickBtn(){
      console.log("普通变量", dataname);
      console.log("reactive变量", leeobj);
      console.log("reactive变量", leeobj.leename);
      console.log("reactive变量", leeobj.leenamecom);
      console.log("ref变量", refname);
    }

    return {
      dataname,
      // 使用torefs前在页面模板中需要，leeobj.leename
      // leeobj,
      // 使用torefs后在页面模板中需要，leename
      ...toRefs(leeobj),
      clickBtn
    };
  },
};
</script>