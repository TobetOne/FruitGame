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
  5. result <= 35242: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/apple.png" height="30px" width="30px"/><br>
     result <= 52024: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/apple_s.png" height="30px" width="30px"/><br>
     result <= 69645: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/orange.png" height="30px" width="30px"/><br>
     result <= 86427: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/orange_s.png" height="30px" width="30px"/><br>
     result <= 98174: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/pawpaw.png" height="30px" width="30px"/><br>
     result <= 114956: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/pawpaw_s.png" height="30px" width="30px"/><br>
     result <= 123767: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bell.png" height="30px" width="30px"/><br>
     result <= 140549: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bell_s.png" height="30px" width="30px"/><br>
     result <= 149360: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/watermelon.png" height="30px" width="30px"/><br>
     result <= 166142: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/watermelon_s.png" height="30px" width="30px"/><br>
     result <= 172016: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/star.png" height="30px" width="30px"/><br>
     result <= 188798: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/star_s.png" height="30px" width="30px"/><br>
     result <= 193203: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/77.png" height="30px" width="30px"/><br>
     result <= 209985: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/77_s.png" height="30px" width="30px"/><br>
     result <= 213509: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bar_s.png" height="30px" width="30px"/><br>
     result <= 215271: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bar.png" height="30px" width="30px"/><br>
     result <= 215605: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/sixi.png" height="30px" width="30px"/><br>
     result <= 215772: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/smallternary.png" height="30px" width="30px"/><br>
     result <= 215922: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/largeternary.png" height="30px" width="30px"/><br>
     result <= 216122: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bar_s.png" height="30px" width="30px"/><br>
     result <= 216247: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/bar.png" height="30px" width="30px"/><br>
     result <= 216272: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/all.png" height="30px" width="30px"/><br>
     else: <img src="https://github.com/TobetOne/FruitGame/blob/master/image/none.png" height="30px" width="30px"/><br>

## 随机因子说明
   seed = GameId+BetPlayersCount+BetAmount*10000+LastBetTime
*  GameId:游戏ID
*  BetPlayersCount:参与游戏玩家个数
*  BetAmoun:本局游戏玩家总投注金额
*  LastBetTime:玩家的投注时间
## 签名验证
   验证签名使用Tobet的公钥（EOS6CG8VwJ8G1iFn6x781PMojmfD7i4kqqzsgd1AjWwAaEz35QGhn），对seed_sign进行ecc签名验证，验证结果通过即可证明随机种子未被篡改。
