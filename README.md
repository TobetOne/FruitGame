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
  5. result <= 35242: apple
     result <= 52024: smallapple
     result <= 69645: orange
     result <= 86427: smallorange
     result <= 98174: pawpaw
     result <= 114956: smallpawpaw
     result <= 140549: smallbell
     result <= 149360: watermelon
     result <= 166142: smallwatermelon
     result <= 172016: doublestar
     result <= 188798: smalldoublestar
     result <= 193203: sevenseven
     result <= 209985: smallsevenseven
     result <= 213509: smallbar
     result <= 215271: largebar
     result <= 215605: sixi
     result <= 215772: smallternary
     result <= 215922: largeternary
     result <= 216122: giftsmallbar
     result <= 216247: giftlargebar
     result <= 216272: perfect
     else: none

## 随机因子说明
   seed = GameId+BetPlayersCount+BetAmount*10000+LastBetTime
*  GameId:游戏ID
*  BetPlayersCount:参与游戏玩家个数
*  BetAmoun:本局游戏玩家总投注金额
*  LastBetTime:玩家的投注时间
## 签名验证
   验证签名使用Tobet的公钥（EOS6CG8VwJ8G1iFn6x781PMojmfD7i4kqqzsgd1AjWwAaEz35QGhn），对seed_sign进行ecc签名验证，验证结果通过即可证明随机种子未被篡改。
