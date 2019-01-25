# Tobet FruitGame Verify

验证工具网页请访问：https://tobetone.github.io/FruitGame/

在使用此网页工具之前，请仔细阅读以下说明。你可以根据如下说明，自行开发程序验证。
## 开奖结果计算
  1. 根据游戏数据生成随机种子,并签名：  
    seed = GameId+BetPlayersCount+BetAmount*10000+LastBetTime;  
    seed_sign = sign(seed)  
  2. 对随机种子hash（SH256）运算，结果转换为16进制  
    hash_hex = hex(sha256(seed_sign))   
  3. 对hash_hex计算hashcode
  4. result = Abs(hashcode%220264) + 1
  5. result <= 35242: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/apple.png)<br>
     result <= 52024: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/apple_s.png)<br>
     result <= 69645: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/orange.png)<br>
     result <= 86427: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/orange_s.png)<br>
     result <= 98174: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/pawpaw.png)<br>
     result <= 114956: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/pawpaw_s.png)<br>
     result <= 123767: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bell.png)<br>
     result <= 140549: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bell_s.png)<br>
     result <= 149360: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/watermelon.png)<br>
     result <= 166142: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/watermelon_s.png)<br>
     result <= 172016: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/star.png)<br>
     result <= 188798: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/star_s.png)<br>
     result <= 193203: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/77.png)<br>
     result <= 209985: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/77_s.png)<br>
     result <= 213509: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bar_s.png)<br>
     result <= 215271: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bar.png)<br>
     result <= 215605: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/sixi.png)<br>
     result <= 215772: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/smallternary.png)<br>
     result <= 215922: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/largeternary.png)<br>
     result <= 216122: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bar_s.png)<br>
     result <= 216247: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/bar.png)<br>
     result <= 216272: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/all.png)<br>
     else: ![avatar](https://github.com/TobetOne/FruitGame/blob/master/image/none.png)<br>

## 随机因子说明
   seed = GameId+BetPlayersCount+BetAmount*10000+LastBetTime
*  GameId:游戏ID
*  BetPlayersCount:参与游戏玩家个数
*  BetAmoun:本局游戏玩家总投注金额
*  LastBetTime:玩家的投注时间
## 签名验证
   验证签名使用Tobet的公钥（EOS6CG8VwJ8G1iFn6x781PMojmfD7i4kqqzsgd1AjWwAaEz35QGhn），对seed_sign进行ecc签名验证，验证结果通过即可证明随机种子未被篡改。
