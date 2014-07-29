Highcharts-Learning
===================

Highcharts  is an effeciently tool for developers to make the best charts. you can easily finish pie charts,column charts etc. 

###<a href="">pie charts animation[lables and plots moved by mouse action]</a>
HighCharts provide a default aniamation when using pie charts. The data plot can go away from the central part.
<a href="">see details</a>

```html
point: {
	events: {
	    click: function(){
	        
	    },

	    mouseOver: function(e) {
	        
	        $(this.dataLabel).stop(true,true);
	        this.slice(true, true, true);

	        var translation = this.slicedTranslation||{
	            translateX: 0,
	            translateY: 0
	        }
	        var dlTranslation = {
	            translateX: this.dataLabel.translateX + translation.translateX,
	            translateY: this.dataLabel.translateY + translation.translateY,
	        };
	        console.log(dlTranslation);
	        this.dataLabel.animate(dlTranslation);
	        this.connector.animate(translation);

	    },
	    mouseOut: function() {
	        $(this.dataLabel).stop(true,true);
	        this.slice(false, true, true);
	        var translation = this.slicedTranslation||{
	            translateX: 0,
	            translateY: 0
	        };
	    
	        


	        var dlTranslation = {
	            translateX: this.dataLabel.translateX - translation.translateX,
	            translateY: this.dataLabel.translateY - translation.translateY
	        };
	        console.log(dlTranslation);
	        translation = {
	            translateX: 0,
	            translateY: 0
	        }
	       this.dataLabel.animate(dlTranslation);
	        
	        this.connector.animate(translation);
	    }
	}
}

```
