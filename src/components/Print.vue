<template>
	<div class="col text-center">
		<button @click="makePDF" class="btn btn-success">정답보기</button>
		<button @click="makePDF" class="btn btn-success">다운로드</button>
		<button @click="makePDF" class="btn btn-info">출력하기</button>
		<div data-html2canvas-ignore="true">출력하지 않고 싶은 영역은 태그에 'data-html2canvas-ignore' attribute를 넣어주면된다.</div>
	</div>
</template>

<script>
import html2canvas from 'html2canvas'
import jsPDF from 'jspdf'

export default {
	name: 'pdf',
	data () {
		return {
			propTitle: 'mypdf'
		}
	},
	methods: {
		makePDF () {
			window.html2canvas = html2canvas //Vue.js 특성상 window 객체에 직접 할당해야한다.
			let that = this
			let pdf = new jsPDF('p', 'mm', 'a4')
			let canvas = pdf.canvas
			const pageWidth = 210 //캔버스 너비 mm
			const pageHeight = 295 //캔버스 높이 mm
			canvas.width = pageWidth
      let ele = document.querySelector('#PrintAAAA')
			let width = ele.offsetWidth // 셀렉트한 요소의 px 너비
			let height = ele.offsetHeight // 셀렉트한 요소의 px 높이
			let imgHeight = pageWidth * height/width // 이미지 높이값 px to mm 변환
      if(!ele){
				console.warn( ' is not exist.')
				return false
			}

			//html2canvas(ele,{});
			html2canvas(ele).then(function(canvas) {
				let position = 0
				const imgData = canvas.toDataURL('image/png')
				pdf.addImage(imgData, 'png', 0, position, pageWidth, imgHeight, undefined, 'slow')
					//Paging 처리
				let heightLeft = imgHeight //페이징 처리를 위해 남은 페이지 높이 세팅.
				heightLeft -= pageHeight
				while (heightLeft >= 0) {
					position = heightLeft - imgHeight
					pdf.addPage();
					pdf.addImage(imgData, 'png', 0, position, pageWidth, imgHeight)
					heightLeft -= pageHeight
				}

				pdf.save(that.propTitle.toLowerCase() +'.pdf')

		  });



		},
	}
}
</script>
<link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.1.3/css/bootstrap.min.css">
