(function($) {

	$.fn.contentSlider = function(options){
	  
		// default configuration properties
		var defaults = {	
			fx:                     'fade',			
			speed: 			1000,
			auto:			false,
			pause:			3000,
			continuous:		false
		}; 
		
		var options = $.extend(defaults, options);  				
		this.each(function() {  
			var obj = $(this); 						
			var s = $("div.one", obj).length;
			var w = $("div.one", obj).width(); 
			var h = $("div.one", obj).height(); 
			var elements = $("div.one",obj);
			obj.width(w); 
			obj.height(h); 
			obj.css("overflow","hidden");
			var ts = s-1;
			var t = 0;
			
			if(options.fx == 'fade'){  			 
			    for (var i = 0; i < elements.length; i++) {
				$(elements[i]).css('z-index', String(elements.length-i)).css('position', 'absolute').hide();
			    };
                        }
			if(options.fx == 'slide'){
			       $("div.one", obj).css('float','left');	
			}					
		

			$("a","#"+options.nextId).click(function(){		
				animate("next",true);
			});

			$("#li_1").click(function(){		
				animate("one",true);
			});
			$("#li_2").click(function(){		
				animate("two",true);				
			});	

			$("#li_3").click(function(){		
				animate("three",true);
			});				
			$("#li_4").click(function(){		
				animate("four",true);				
			});			
			
			function animate(dir,clicked){
				 var ot = t;				
				switch(dir){
					case "next":
						t = (ot>=ts) ? (options.continuous ? 0 : ts) : t+1;					
						break; 
					case "one":											
						t = 0 ; 
					       clearTimeout(timeout); 
					       timeout =  setTimeout(function() {
						    animate("next",false);
						}, options.pause);							
						break; 
					case "two":						
						t = 1 ;
						clearTimeout(timeout); 
					       timeout =  setTimeout(function() {
						    animate("next",false);
						}, options.pause);
						break; 
					case "three":
						t = 2;
						clearTimeout(timeout); 
					       timeout =  setTimeout(function() {
						    animate("next",false);
						}, options.pause);
						break; 
					case "four":
						t = ts;
						clearTimeout(timeout); 
					       timeout =  setTimeout(function() {
						    animate("next",false);
						}, options.pause);
						break; 
					default:
						break; 
				};
				
				jQuery("#li_"+(ot+1).toString()).attr("class","");
				jQuery("#li_"+(t+1).toString()).attr("class","selected_color");	
	
				
				var diff = Math.abs(ot-t);
				var speed = diff*options.speed;						
			
					op = (ot*w*-1);
					p = (t*w*-1);
		
			if(options.fx == 'fade'){				 			$(elements[ot]).fadeOut(options.speed);           
		                $(elements[t]).fadeIn(options.speed);	
					}
			

			if(options.fx == 'slide'){
				if(p == 0){ // 返回到第一张图片 , 变class
						jQuery("#li_1").attr("class","selected_color");	
						speed = speed/4 ; // 加快第4张到第一张间的滑动速度
					}
				   $("div.index_ad_content",obj).animate(
						{ marginLeft: p }, 
						speed
					);

					}
       						
						
				
				
				// if(clicked) clearTimeout(timeout); // 点击后 停止滚动
				if(options.auto && dir=="next" && !clicked){;	
					timeout = setTimeout(function(){
						animate("next",false);
					},diff*options.speed+options.pause);
				};
				
			};
			
			// init
			var timeout;
			if(options.auto){;
               timeout =  setTimeout(function() {
                    animate("next",false);
                }, options.pause);
		$(elements[0]).show();                
			};							
			
		});	  
	};
})(jQuery);



