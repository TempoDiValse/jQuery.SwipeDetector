(function(window, $){
	var DirectionType = {
		left: 'left',
		right: 'right',
		none: 'none'
	};

	var options = {
		threshold: 100,
		exceptArea: [],
		callback: null
	}

	var methods = {
		init: function(_options){
			$.extend(options, _options);

			wrapper = this;

			wrapper.bind('touchstart touchmove touchend', onTouchListener);
		},
		setOption : function(optName, value){
			if(optName == 'threshold'){
				value = calculateThreshold(value);
			}

			options[optName] = value;
		}
	}

	var wrapper = this;
	var callback;
	var direction = DirectionType.none;

	$.fn.detect = function(method){
		if(!method || method == "" ||typeof method === 'object'){
			return methods.init.apply(this,arguments);
		}else if(methods[method]){
			return methods[method].apply(this, Array.prototype.slice.call(arguments, 1));
		}
	}
	
	var px, py;
	function onTouchListener(e){
		var type = e.type;
		var touches = e.originalEvent.touches[0];
		var threshold = options.threshold;
		var exceptArea = options.exceptArea;
		
		if(exceptArea.length != 0){
			for(var i=0; i<exceptArea.length; i++){
				if(exceptArea[i] == e.target.id){
					return;
				}
			}
		}
		
		if(type == "touchstart"){
			px = touches.pageX;
		}else if(type == "touchmove"){
			var distX = touches.pageX - px;

			if(distX >= threshold){
				direction = DirectionType.right;
			}else if(distX <= -threshold){
				direction = DirectionType.left;
			}else{
				direction = DirectionType.none;
			}
		}else{
			options.callback.call(this, direction);
		}
	}

	function calculateThreshold(value){
		return $(window).width() / value;
	}
})(window, jQuery);
