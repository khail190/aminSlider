aminSlider
==========

Javascript Simple Automatic Slider Using Jquery

<pre>
&lt;style&gt;
    .aminSlider{
        width: 316px;
        height: 697px;
        margin: 20px auto;
        overflow: hidden;
    }
    .aminSlider .slidePanel{
        position: relative;
    }
    .aminSlider .mobile{
        width: 316px;
        height: 697px;
    }
    .aminSlider .bullet{
        background: url(&quot;/images/introbullet.png&quot;);
        background-position: top;
        width: 19px;
        height: 20px;
        display: inline-table;
    }
    .aminSlider .bullet:hover, .aminSlider .bullet.active{
        background-position: bottom;
    }
    .aminSlider .numbers{
        position: relative;
        text-align: center;
        top: -235px;
    }
&lt;/style&gt;
&lt;div class=&quot;wrap&quot;&gt;
    &lt;div class=&quot;home-content&quot;&gt;
        &lt;div class=&quot;aminSlider&quot;&gt;
            &lt;div class=&quot;slidePanel&quot;&gt;
                &lt;img class=&quot;mobile&quot; src=&quot;/images/mobileimage1.png&quot; /&gt;
                &lt;img class=&quot;mobile&quot; src=&quot;/images/mobileimage2.png&quot; /&gt;
                &lt;img class=&quot;mobile&quot; src=&quot;/images/mobileimage3.png&quot; /&gt;
                &lt;img class=&quot;mobile&quot; src=&quot;/images/mobileimage4.png&quot; /&gt;
            &lt;/div&gt;
            &lt;div class=&quot;numbers&quot;&gt;
                &lt;a href=&quot;#_&quot; class=&quot;bullet active&quot;&gt;&lt;/a&gt;
                &lt;a href=&quot;#_&quot; class=&quot;bullet&quot;&gt;&lt;/a&gt;
                &lt;a href=&quot;#_&quot; class=&quot;bullet&quot;&gt;&lt;/a&gt;
                &lt;a href=&quot;#_&quot; class=&quot;bullet&quot;&gt;&lt;/a&gt;
            &lt;/div&gt;
        &lt;/div&gt;
        &lt;div&gt;&lt;a href=&quot;#_&quot; onClick=&quot;amin1.prevSlide()&quot;&gt;Previous&lt;/a&gt;&lt;/div&gt;
        &lt;div&gt;&lt;a href=&quot;#_&quot; onClick=&quot;amin1.nextSlide()&quot;&gt;Next&lt;/a&gt;&lt;/div&gt;
&lt;/div&gt;
&lt;/div&gt;
&lt;script&gt;
            function aminSlider()
            {
                var imageCount = 2, currentSlide = 0, pp = &quot;.aminSlider&quot;,mobileWidth=0,timer=null,api='',timeOfTimer=4000;

                this.init = function()
                {
                    imageCount = $(pp + &quot; .mobile&quot;).length;
                    mobileWidth = parseInt($(pp + &quot; .mobile&quot;).eq(0).css(&quot;width&quot;));
                    $(pp + &quot; .slidePanel&quot;).css({width: (mobileWidth * imageCount) + (4 * imageCount)});

                    $(pp + &quot; .numbers a&quot;).each(function(index) {
                        $(this).click(function() {
                            currentSlide = index;
                            slide.call(this);
                            $(pp + &quot; .numbers a&quot;).removeClass(&quot;active&quot;);
                            $(this).addClass(&quot;active&quot;);
                        });
                    });
                    
                    timer = setTimeout(api+'.nextSlide()',timeOfTimer);
                }

                slide = function()
                {
                    if (currentSlide &gt;= imageCount)
                        currentSlide = 0;
                    if (currentSlide &lt; 0)
                        currentSlide = imageCount - 1;

                    $(pp + &quot; .slidePanel&quot;).stop().animate({
                            left: -(mobileWidth*currentSlide)-(4 * currentSlide)
                        }, 1000, 'easeInOutBack', function() {
                    });
                    
                    clearTimeout(timer);
                    timer = setTimeout(api+'.nextSlide()',timeOfTimer);
                }

                this.nextSlide = function()
                {
                    currentSlide++;
                    slide.call(this);
                    $(pp + &quot; .numbers a&quot;).removeClass(&quot;active&quot;);
                    $(pp + &quot; .numbers a&quot;).eq(currentSlide).addClass(&quot;active&quot;);
                }

                this.prevSlide = function()
                {
                    currentSlide--;
                    slide.call(this);
                    $(pp + &quot; .numbers a&quot;).removeClass(&quot;active&quot;);
                    $(pp + &quot; .numbers a&quot;).eq(currentSlide).addClass(&quot;active&quot;);
                }
                
                this.setApi = function(newApi){
                    api = newApi;
                }
            }

            $(document).ready(function() {
                amin1 = new aminSlider();
                amin1.setApi('amin1');
                amin1.init();
            });

            function cl()
            {
                for (var i = 0; i &lt; arguments.length; i++) {
                    console.log(arguments[i]);
                }
            }
&lt;/script&gt;
  </pre>
