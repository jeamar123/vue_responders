<script>
	import axios from 'axios'
	import GoogleMapsApiLoader from 'google-maps-api-loader'
	import * as config from '@/config';

	var gmap = {
		data() {
			return {
				showLoader : false,
				google: null,
				mapConfig: {
					center: {lat: -34.397, lng: 150.644},
          zoom: 8
				},
				apiKey: config.gmapApiKey,
				infoWindow: null,
			}
		},
		async mounted() {
	    const googleMapApi = await GoogleMapsApiLoader({
	      apiKey: this.apiKey
	    })
	    this.google = googleMapApi
	    
	    this.initializeMap();
	  },
		created() {

		},
		methods: {
      showLoading() {
      	this.showLoader = true;
      },
      hideLoading() {
      	setTimeout(()=>{
				  this.showLoader = false;
				},1000);
      },
      initializeMap() {
	      const mapContainer = this.$refs.googleMap;
	      this.map = new this.google.maps.Map(mapContainer, this.mapConfig);
      	this.getGeoLocation();
	    },
	    getGeoLocation(){
	    	console.log( this.map );
	    	var infoWindow = new google.maps.InfoWindow;
        // Try HTML5 geolocation.
        if (navigator.geolocation) {
          navigator.geolocation.getCurrentPosition((position) => {
            var pos = {
              lat: position.coords.latitude,
              lng: position.coords.longitude
            };
            infoWindow.setPosition(pos);
            infoWindow.setContent('Location found.');
            infoWindow.open(this.map);
            this.map.setCenter(pos);
          },() => {
            this.handleLocationError(true, infoWindow, this.map.getCenter());
          });
        } else {
          // Browser doesn't support Geolocation
          this.handleLocationError(false, infoWindow, this.map.getCenter());
        }
	    },
	    handleLocationError(browserHasGeolocation, infoWindow, pos) {
        infoWindow.setPosition(pos);
        infoWindow.setContent(browserHasGeolocation ?
                              'Error: The Geolocation service failed.' :
                              'Error: Your browser doesn\'t support geolocation.');
        infoWindow.open(this.map);
      }


    }
	}

	export default gmap;
</script>