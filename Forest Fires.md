森林火灾
=========
Forest Fires
-----------------

在TS里树木被带有`Sparky=yes`的弹头攻击后会起火，同时将火势蔓延到周围的树上，以此造成森林火灾，HARES恢复了这个功能，不过需要一些设置。
 
你需要在每个可燃烧的树上写上`IsFlammable=yes`，并且设置好`[AudioVisual]►OnFire`的三个动画以及`[AudioVisual]►TreeFire`的两个动画
 
如果烧不掉树，注意`[AudioVisual]►SmallFire`的动画在Art需要设置`Scorch=no`