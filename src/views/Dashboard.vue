<template>
	<div id="main-content" >
	  <div class="navbar">
	  	header
	  </div>

	  <div class="child-content">
	  	<router-view></router-view>
	  </div>

	  <transition name="fade">		
		  <div v-if="showLoader" class="main-loader">
				<div class="circle-loader">
					<div class="preloader-container">
						<div class="preloader-wrapper big active">
					    <div class="spinner-layer spinner-blue-only">
					      <div class="circle-clipper left">
					        <div class="circle"></div>
					      </div><div class="gap-patch">
					        <div class="circle"></div>
					      </div><div class="circle-clipper right">
					        <div class="circle"></div>
					      </div>
					    </div>
					  </div>
					</div>
				</div>
			</div>
		</transition>
  </div>
  
</template>

<script>
	import dashboard from '@/components/dashboard'
	export default dashboard
</script>
