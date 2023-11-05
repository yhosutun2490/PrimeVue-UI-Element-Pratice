<script setup>
import {ref,defineProps,useSlots,getCurrentInstance, watch} from 'vue'
// 設定資料狀態
const resData = ref("")
const isLoading = ref(true)
// slot instance
const slot = useSlots()
// props from parent
const props = defineProps({
  url: {
    Type: String
  },
  watchValue: {
    Type: String
  }
})
FetchApi()
watch(()=>props.watchValue,()=> {
  console.log("觸發call 貓貓api")
  FetchApi()
})
// fetch function
function FetchApi () {
  fetch(props.url)
    .then(res => res.json())
    .then(res => {
      resData.value = res
      isLoading.value = false
      console.log("res貓貓", res)
    })

}

// return fetch data to slot
getCurrentInstance().render = () => {
  return slot.default({
    res: resData.value,
    loading: isLoading.value
  })
}
</script>
