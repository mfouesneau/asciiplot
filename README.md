AP - Package that allows you to plot simple graphs in ASCII, a la matplotlib.
============================================================================

This package is a inspired from Imri Goldberg's ASCII-Plotter 1.0 (https://pypi.python.org/pypi/ASCII-Plotter/1.0)

At a time I was enoyed by security not giving me direct access to my computer, and thus to quickly make figures from python, I looked at how I could make quick and dirty ASCII figures. But if I were to develop something, I wanted something that can be used with just python and possible standard-ish packages (numpy, scipy).

So I came up with this package after many iterations based of ASCII-plotter.  I added the feature to show multiple curves on one plot with different markers.  And I also made the usage, close to matplotlib, such that there is a plot, hist, hist2d and imshow functions.


TODO:
-----
* [ ] imshow does not plot axis yet.
* [ ] make a correct documentation
* [x] publish on github


available markers
-----------------
	|marker  |  repr   | unicode     |     description                 | 
	|--------|---------|-------------|---------------------------------|
	|'-'     |         | u'None'     |  solid line style               |
	|','     |   ∙     | u'\u2219'   |  point marker                   |
	|'.'     |   ∘     | u'\u2218'   |  pixel marker                   |
	|'o'     |   ○     | u'\u25CB'   |  circle marker                  |
	|'of'    |   ●     | u'\u25CF'   |  circle marker                  |
	|'v'     |   ▽     | u'\u25BD'   |  triangle_down marker           |
	|'vf'    |   ▼     | u'\u25BC'   |  filler triangle_down marker    |
	|'^'     |   △     | u'\u25B3'   |  triangle_up marker             |
	|'^f'    |   ▲     | u'\u25B2'   |  filled triangle_up marker      |
	|'<'     |   ◁     | u'\u25C1'   |  triangle_left marker           |
	|'<f'    |   ◀     | u'\u25C0'   |  filled triangle_left marker    |
	|'>'     |   ▷     | u'\u25B7'   |  triangle_right marker          |
	|'>f'    |   ▶     | u'\u25B6'   |  filled triangle_right marker   |
	|'s'     |   ◽     | u'\u25FD'   |  square marker                  |
	|'sf'    |   ◼     | u'\u25FC'   |  square marker                  |
	|'*'     |   ☆     | u'\u2606'   |  star marker                    |
	|'*f'    |   ★     | u'\u2605'   |  star marker                    |
	|'+'     |   ✚     | u'\u271A'   |  plus marker                    |
	|'x'     |   ❌     | u'\u274C'   |  x marker                       |
	|'d'     |   ◇     | u'\u25C7'   |  diamond marker                 |
	|'df'    |   ◆     | u'\u25C6'   |  filled diamond marker          |


Examples
--------
* plot

```python
In [1]: import ap
In [2]: import numpy as np
In [3]: p = AFigure(**flags)
In [4]: x = np.arange(10)
In [5]: y = x ** 2 
In [6]: _ = p.plot(x, y, marker='_o', plot_slope=plot_slope)
In [7]: print p.plot(x, 30. - y, marker='_s')

  │                                               
  ┼+79.548                                     ○  
  │                                               
  │                                       ○       
  │                                               
  │                                  ○            
  │                                               
  │                             ○                 
  ◽    ◽    ◽              ○                      
  │              ◽    ○                           
  │              ○    ◽                           
──┼────○────○──────────────◽───────────────────┼──
  │+0.046                       ◽      +8.97638   
  │                                               
  │                                  ◽            
  │                                               
  │                                       ◽       
  ┼-48.228                                        
  │                                            ◽  
  │                                               
```

* hist

```python

In [1]: import ap, numpy as np
In [2]: x = np.random.normal(0, 1, 1e6)
In [3]: ap.hist(x, 20)
                        │                         
                       ∘┼+180303                  
                       |│ ∘                       
                       |│ |                       
                     ∘ |│ |                       
                     | |│ | ∘                     
                     | |│ | |                     
                     | |│ | |                     
                     | |│ | |                     
                  ∘  | |│ | |                     
                  |  | |│ | | ∘                   
                  |  | |│ | | |                   
                  |  | |│ | | |                   
                ∘ |  | |│ | | |                   
                | |  | |│ | | |  ∘                
                | |  | |│ | | |  |                
              ∘ | |  | |│ | | |  | ∘              
           ∘  | | |  | |┼+3828.47| |  ∘           
──┼--------------------------------------------┼──
   -4.39861             │              +4.48165   

In [4]: x = np.random.normal(0, 1, 1e6)
In [5]: ap.hist2d(x, y, bins=[20,20], width=30)
                              
                              
             ....             
           ..;;;;..           
         ..;-----;;.          
         .;-:!>>!:-;.         
        .;-!>???7>:-;.        
        .-:>?O$$O?>:;.        
       .;-!7OQHHQO7!-.        
       .;->?$HMNH$?!-..       
       .;->?$HNNH$?!-..       
       .;-!7OQHHQO7!-.        
        .;:>?O$$C?>:;.        
        .;-:>7??7>:-;.        
         .;-:!!!!:-;.         
          .;;----;;.          
           ...;;...           
              ..              
                              

```

* imshow

```python
In [1]: import ap
In [2]: from scipy import misc
In [3]: im = misc.lena()
In [4]: ap.imshow(im.T)
OOCCOO>!!>>7777??777?77?777777>>CCCCCCCHN!77>777>7
CCCCOO>!!!>777777?7?7777777777>!CCCCCCCON>>>>777!.
CCCOOC>:!!>7777777???7777777777>?OCCCCCCHH!>777!..
CCCOCO>!>!!777777777>7777?7777>>7CCOCCCC?NO>>7!.;.
OOOOCC!!!!!777777777777>777777>>7CCCCCCC?HN!>!.;..
COC?OO!:!!>77777777C?O$$Q>7777>>7?CCCC????NH!.....
OO!COO!:!!>>7777?7?7?OOQ$QQ>77>!7C??C?????QM..;...
O?-COO!:!!!>>77!>7>7?C$$Q$QH:>!>7CC??????CC..;..-7
C!:COC!:!!!>>77>>>>?7?OQ$OHHN-!!7CC>>????C.....-:C
7!:?OC!!!!>>>7!>7>??C?O?HHQHHN-!7CC>;????7.;.;;!CO
:::COC!::!!>>>>>>?C???$QQQQHHHH;7CC>.:??C.;;;.;?CO
:::?OO>:!!!>!!!>7???>QOCQHHHHHHN>CC>. NH..;...CCCC
!!:?OO!-!!!>N:>7?77>$O$$$QQQQHHH:CC>.CNHQ.. ;7?CCC
!!!?OO!:!!>>H!7>7>???OO$O$QHQQHQHCCNQHQHO....CCCCC
!!!?OO>:!!!!$>!>7??7OCCO$OQ$QQQQQQQHHHQH ..;CCCCCC
!!!?OO!:!!!!OC>>??7CCCOOOCO$$$$C$HQQHHCQ.;.:?COCCC
!!!?OO!:!!!:Q????>?7?CO?CCOCOCQQ$QQHHCON...CCCCCCC
!!!?OO!:!!!:QCC>7?77C?:??::-?CQQQQHH$:O..;!?CCCCCC
!!!?OO!:!!!!Q?7!?77??!-::;.7Q$QQQQ$!!$ ;.;?OOCCCCC
!!!COO>:!!!!NOC?>>?>-; ;-:$$O$OQQ:7O$ ...;?OOOOCCC
>!!?OO>:!!!>:Q?>77!:.>-->7QQ$$$$$-?$..;..7OOOCCCCC
!!:?OO>:!!!>>H>77>:.- - >C$O$$QQQ::C.;;.;7COCOOCCC
!!!?O$>:!!!>>N>7!..;;!!C$?QOOQQHH> O;;;.>CCCCCOCC?
!!!?OO>:!!!>>:77.;;. ::OO$COO$QHHC.O;;..?OOOOC??CC
>!!?OO>:!!!>? :;. :.- $QQ?C:?OQQ7:.>;;.;7CCCCCCC?7
!!:?$$>:!!:7C;:;7. 7.!$Q-;;.7CH:;;.--..7CCCCCCC???
!!-?$$>:!!.$.-;:-;.;;CQ>!>H?7?N>$..;!..?CCCCC????$
!:-?$$7!>?:;;7.-?.; >Q!?CCCC77NC7:.;;..7CCCC??7$QQ
::;?$$7:?C:->..>.;.7$.>?OO$O?7NO7>;.;.>CCCC??7QQQQ
--;?O$7!>C>;7;.>.O >$;7?C$OC?7HO?>..C;?OCCC?7$QQHQ
--.7$$>:?-!?7..->.-H ;>7CCO?7>$C?-- C.?CCCC?7QQHHH
---7O$7:>!-;::-.  $.;->7?CC?7:OC7.-.?;CCCC??$QHHHH
:-;CO$7:?!::>?--7-O..>77?CCC?QQ?:.!;O?CC???7QQHHHH
---?O$7:7:-!-> OQ7;;;!>7????C$O?..:;O?CCC??7QHHHHH
;;-C$$7-7;->!->C!. .-->77?77C$?!.;--7?CC???7HHHHHH
;;:?$$7?-.;Q>7>H.;.;;-->7??7>7C.;.:;7CCCC??>NHNHHH
..>?O$7:-;.>>!?H....;.-->7?OOO..;.:-!CCCC?7>NHHHHH
..:?O$>Q.;.C--OC;-...-;-;!7?C7.;-.::>7??C?77NHHQ;.
!.;>O$O- .!.?O!7$;.....:77???$QH..-!O?7>!>>$HH$ -:
??-!O$7;.?- -;77!;;;;.::77??C$QQH!;-O???7>?$HH.-!:
;C7!$$O..;!..;>77N..;.7:????CO$QHH;;????77?HH?!!!!
 CC!$$?.;.C;;-!C.Q-;-;!:????CC$$HHN CC??77QNH:!!!>
 7C:$$?;..!.. >??.:..:>:7???CCO$QHN C???77HNC!>:!!
 >O-$$?..;-..-;>>-.7.>7!7?7??CO$QHH?????7CHH>!!!!!
 :C:O$7;.;;;..;-: -.->:7?????CCOQHHN:>????$H>!:!!;
.;$-O$?;.;.;; 7:.-..!7-??????CCO$QHN::;;>$H?;-:::;
:!$:O$!....-.;;7;. -> 7???????CO$QHH:>!;;QQ.;>->:-
.!$:O$!.... ;;.7:...!>7???????CCO$HHH!!!!O--!:!!;;
.;H!$$-..;..7!;-;.:>777?????C??CO$QHN:>7>!!!-;>:;;
..Q>O$!.;-:.:..;;:!>7777?????CCCOOQHH!!77?:-:>>.->
```
