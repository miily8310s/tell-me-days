<script lang="ts">
import { getDay } from "date-fns";

  import getDaysInMonth from "date-fns/getDaysInMonth";

  let yeanMonth = ''
  let weekDays = []
  let resultDays = []

  function testff() {
    if(yeanMonth !== '' && weekDays.length !== 0) {
      const testMonth = new Date(yeanMonth)
      const testDaysinMonth = getDaysInMonth(testMonth)

      for (let i = 0; i < testDaysinMonth; i++) {
        const testDay = new Date(testMonth.getFullYear(), testMonth.getMonth() , i)
        if ((weekDays.indexOf(getDay(testDay))) > -1) {
          resultDays.push(i)
        }
      }
    }
  }

</script>

<div class="flex flex-col justify-center items-center my-6">
  <h2 class="font-semibold md:text-xl text-md mb-3 px-3">年月と曜日を選択することで該当する日付を教えてくれるアプリです。</h2>
  <div class="shadow-md p-6 w-full md:w-2/3 mb-6 bg-white">
    <div class="flex flex-row items-center sm:text-xl text-sm leading-4 mb-6">
      <label for="" class="mr-10 font-semibold break-normal">年月</label>
      <input type="month" class="h-12 leading-6" bind:value={yeanMonth}>
    </div>
    <div class="flex flex-row items-center sm:text-xl text-sm leading-4 mb-6">
      <label for="weekday" class="mr-9 font-semibold break-normal sm:w-1/12 w-10 xl:w-10">曜日</label>
      <div class="flex flex-row items-center flex-wrap">
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={1}>
          <span>月</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={2}>
          <span>火</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={3}>
          <span>水</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={4}>
          <span>木</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={5}>
          <span>金</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={6}>
          <span>土</span>
        </div>
        <div class="mr-3 mb-2">
          <input type="checkbox" class="transform scale-150" bind:group={weekDays} value={0}>
          <span>日</span>
        </div>
      </div>
    </div>
  </div>
  <button 
    class="md:text-xl text-sm font-semibold leading-4 p-3 text-white bg-blue-500 rounded"
    on:click={testff}
  >
    日付を教えてもらう
  </button>
  <div class="shadow-md p-6 w-full md:w-2/3 mt-14 flex justify-center bg-white">
    <div class="w-full md:w-2/3 py-3 text-2xl text-center border-b border-green-400">
      <input type="text" bind:value={resultDays}>
    </div>
  </div>
</div>