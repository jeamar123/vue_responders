<template>
	<div id="main-content" >
		<div class="header-banner-container">
			
		</div>

		<section class="block-container">
		  <div class="navbar">
		  	<ul>
		  		<router-link tag="li" to="/dashboard/home">
		  			<a>
		  				<i class="fa fa-laptop"></i> 
		  				Dashboard
		  			</a>
		  		</router-link>
		  		<router-link tag="li" to="/dashboard/map">
		  			<a ui-sref="gmap" ui-sref-active="active">
		  				<i class="fa fa-map-marker"></i> 
		  				Map
		  			</a>
		  		</router-link>
		  		<li>
		  			<a>
		  				<i class="fa fa-heartbeat"></i> 
		  				Responders
		  			</a>
		  		</li>
		  		<li>
		  			<a>
		  				<i class="fa fa-users"></i> 
		  				Users
		  			</a>
		  		</li>
		  	</ul>
		  </div>

		  <div class="child-content">
		  	<router-view></router-view>
		  </div>
	  </section>

	  <div class="header-banner-container">
			
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
