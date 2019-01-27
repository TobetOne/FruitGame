# Tobet FruitGame Verify

验证工具网页请访问：https://tobetone.github.io/FruitGame/

在使用此网页工具之前，请仔细阅读以下说明。你可以根据如下说明，自行开发程序验证。
## 开奖结果计算
  1. 根据游戏数据生成随机种子,并签名：  
    seed = GameId+PlayerAccount+BetAmount*10000+BetTime;  
    seed_sign = sign(seed)  
  2. 对随机种子hash（SH256）运算，结果转换为16进制  
    hash_hex = hex(sha256(seed_sign))
  3. result = parseInt(hash_hex.substr(0,8),16)%220264 + 1
  4. 条件|结果|条件|结果
      -|-|-|-
      0<result≤35242|<img src="./image/apple.png" height="30px" width="30px"/>|35242<result≤52024|<img src="./image/apple_s.png" height="30px" width="30px"/>
      52024<result≤69645|<img src="./image/orange.png" height="30px" width="30px"/>|69645<result≤86427|<img src="./image/orange_s.png" height="30px" width="30px"/>
      86427<result≤98174|<img src="./image/pawpaw.png" height="30px" width="30px"/>|98174<result≤114956|<img src="./image/pawpaw_s.png" height="30px" width="30px"/>
      114956<result≤123767|<img src="./image/bell.png" height="30px" width="30px"/>|123767<result≤140549|<img src="./image/bell_s.png" height="30px" width="30px"/>
      140549<result≤149360|<img src="./image/watermelon.png" height="30px" width="30px"/>|149360<result≤166142|<img src="./image/watermelon_s.png" height="30px" width="30px"/>
      166142<result≤172016|<img src="./image/star.png" height="30px" width="30px"/>|172016<result≤188798|<img src="./image/star_s.png" height="30px" width="30px"/>
      188798<result≤193203|<img src="./image/77.png" height="30px" width="30px"/>|193203<result≤209985|<img src="./image/77_s.png" height="30px" width="30px"/>
      209985<result≤213509|<img src="./image/bar_s.png" height="30px" width="30px"/>|213509<result≤215271|<img src="./image/bar.png" height="30px" width="30px"/>
      215271<result≤215605|<img src="./image/sixi.png" height="30px" width="30px"/>|215605<result≤215772|<img src="./image/smallternary.png" height="30px" width="30px"/>
      215772<result≤215922|<img src="./image/largeternary.png" height="30px" width="30px"/>|215922<result≤216122|<img src="./image/bar_s.png" height="30px" width="30px"/>
      216122<result≤216247|<img src="./image/bar.png" height="30px" width="30px"/>|216247<result≤216272|<img src="./image/all.png" height="30px" width="30px"/>
      216272<result≤220264|<img src="./image/none.png" height="30px" width="30px"/>

## 随机因子说明
   seed = GameId+PlayerAccount+BetAmount*10000+BetTime
*  GameId:游戏ID
*  PlayerAccount:玩家账号
*  BetAmount:本局游戏玩家总投注金额
*  BetTime:玩家的投注时间
## 签名验证
   验证签名使用Tobet的公钥（EOS6CG8VwJ8G1iFn6x781PMojmfD7i4kqqzsgd1AjWwAaEz35QGhn），对seed_sign进行ecc签名验证，验证结果通过即可证明随机种子未被篡改。
