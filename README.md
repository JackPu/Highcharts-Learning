Highcharts-Learning
===================

Highcharts  is an effeciently tool for developers to make the best charts. you can easily finish pie charts,column charts etc. 

###pie charts animation lables and plots moved by mouse action
HighCharts provide a default aniamation when using pie charts. The data plot can go away from the central part.


```html
point: {
	events: {git 
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


see demo[<a href="http://codepen.io/Jack_Pu/pen/sywfJ">Codepen</a>]

### hide highchart logo 

Hiding highchart.com logo is so easy !

``` javascript 
  // add this configuration
  credits: {
      enabled: false
  }

```

### set maxPointWidth

You can Set max width of  coloums chart by using these code.
``` javascript
 (function(H) {
     var each = H.each;
     H.wrap(H.seriesTypes.column.prototype, 'drawPoints', function(proceed) {
         var series = this;
         if (series.data.length > 0) {
             var width = series.barW > series.options.maxPointWidth ? series.options.maxPointWidth : series.barW;
             each(this.data, function(point) {
                 point.shapeArgs.x += (point.shapeArgs.width - width) / 2;
                 point.shapeArgs.width = width;
             });
         }
         proceed.call(this);
     })
 })(Highcharts);
```

Then you can set your highcharts `series` options:

``` javascript
series: [{  
  // ....
    data: data['series']['stars'],
    tooltip: {
        valueSuffix: ' 颗'
    },
    maxPointWidth: 30,  //  最大宽度 采用svg宽度

}]
```




