# csPortfolio
* WebPage [here](https://bartzc.github.io/bartzPhotography/websiteMain.html)
* Lightning [here](https://bartzc.github.io/lightning2/)
* Lightning JS [here](https://bartzc.github.io/bartzPhotography/websiteMain.html)
* Dice [here](https://bartzc.github.io/dice3/)
* Dice JS [here](https://bartzc.github.io/dice3/dice2.pde)

```html

.content-container{
           position:relative; -webkit-perspective:1000; perspective: 1000;
       }
       .content{
           width: 1100px; height: 600px; position: relative; float: left; margin: 35px; -webkit-transition: all 1s ease; transition: all 1s ease; -webkit-transform-style: preserve-3d; transform-style: preserve-3d; 
       }
       .center:hover{
           transform: rotateY(180deg);
           -webkit-transform: rotateY(180deg);
       }
       .center{
           width: 1100px; height: 600; position: absolute;  backface-visibility: hidden; -webkit-backface-visibility: hidden;
       }
       .front{
           z-index: 2;
           background-image: url(IMG_1069.JPG);
       }
       .back{
           -webkit-transform: rotateY(180deg);
           transform: rotateY(180deg);
       }
       #back{
           background: #FFF;
       }
```
