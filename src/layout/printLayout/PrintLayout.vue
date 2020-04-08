<<template>
  <div>
    <Print></Print>
    <Axios v-on:axiosData="parents"></Axios>
    <PrintLayout :dataOfChild="{result}"></PrintLayout>
  </div>
</template>

<script>
import Vue from 'vue'
import Axios from '@/components/Axios'
import Print from '@/components/Print'



export default {
  name: 'SingleDigit',
  data() {
    return {
        result: "cc"
    }
  },
  components: {
    Print,
    Axios

  },
  methods: {
    parents(message){
      this.result = message
    }
  }
}
</script>

<style>
.example[data-v-f3f3eg9] {
  color: red;
}
</style>
