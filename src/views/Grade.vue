<template>
  <div>
    <base-header type="gradient-success" class="pb-6 pb-8 pt-5 pt-md-8">
        <!-- Card stats -->
        <div class="row">
            <div class="col-xl-3 col-lg-6">
                <stats-card title="Total traffic"
                            type="gradient-red"
                            sub-title="350,897"
                            icon="ni ni-active-40"
                            class="mb-4 mb-xl-0"
                >

                    <template slot="footer">
                        <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 3.48%</span>
                        <span class="text-nowrap">Since last month</span>
                    </template>
                </stats-card>
            </div>
            <div class="col-xl-3 col-lg-6">
                <stats-card title="Total traffic"
                            type="gradient-orange"
                            sub-title="2,356"
                            icon="ni ni-chart-pie-35"
                            class="mb-4 mb-xl-0"
                >

                    <template slot="footer">
                        <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 12.18%</span>
                        <span class="text-nowrap">Since last month</span>
                    </template>
                </stats-card>
            </div>
            <div class="col-xl-3 col-lg-6">
                <stats-card title="Sales"
                            type="gradient-green"
                            sub-title="924"
                            icon="ni ni-money-coins"
                            class="mb-4 mb-xl-0"
                >

                    <template slot="footer">
                        <span class="text-danger mr-2"><i class="fa fa-arrow-down"></i> 5.72%</span>
                        <span class="text-nowrap">Since last month</span>
                    </template>
                </stats-card>

            </div>
            <div class="col-xl-3 col-lg-6">
                <stats-card title="Performance"
                            type="gradient-info"
                            sub-title="49,65%"
                            icon="ni ni-chart-bar-32"
                            class="mb-4 mb-xl-0"
                >

                    <template slot="footer">
                        <span class="text-success mr-2"><i class="fa fa-arrow-up"></i> 54.8%</span>
                        <span class="text-nowrap">Since last month</span>
                    </template>
                </stats-card>
            </div>
        </div>
    </base-header>
    <div class="container-fluid mt--7">
        <div class="row">
            <div class="col">
                <gradeonetable title="Light Table"
                               v-if="grade === '1'"
                               @grade="setGrade"
                >
                </gradeonetable>
                <gradetwotable title="Light Table"
                               v-if="grade === '2'"
                >
                </gradetwotable>
                <printLayout  title="Light Table"
                              v-if="grade === '1_1'"
                              :dataOfChild="result"
                >
                </printLayout>
            </div>
        </div>
    </div>

  </div>
</template>

<script>
import gradeonetable from '@/views/Tables/Gradeonetable'
import gradetwotable from '@/views/Tables/Gradetwotable'
import printLayout from '@/layout/printLayout/PrintLayout2'

var data = {"a" : 2}

export default {
  name: 'tables',
  data() {
    return {
      grade: this.$route.query.grade,
      result: data
    }
  },
  components: {
    gradeonetable,
    gradetwotable,
    printLayout
  },
  methods:{
    setGrade: function (grade) {
      this.grade = grade
    }
  }
};
</script>

<style></style>
