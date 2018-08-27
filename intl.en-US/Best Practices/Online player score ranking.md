# Online player score ranking {#concept_pw5_dsn_tdb .concept}

## Scenario introduction {#section_bhs_nyv_wdb .section}

ApsaraDB for Redis functions basically the same as Redis. You can use this product to create a ranking function for an online game easily.

**Sample Code**

```
import java.util.ArrayList;
import java.util.List;
import java.util.Set;
import java.util.UUID;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.Tuple;
public class GameRankSample {
    static int TOTAL_SIZE = 20;
    Public static void main (string [] ARGs) 
    
        //Connection information, obtained from the console.
        String host = "xxxxxxxxxx.m.cnhz1.kvstore.aliyuncs.com";
        int port = 6379;
        Jedis jedis = new Jedis(host, port);
        try {
            //Instance password
            String authString = jedis.auth("password");//password
            if (! authString.equals("OK"))
            
                System.err.println("AUTH Failed: " + authString);
                return;
            
            //Key
            String key = "Game name: Keep Running, Ali!" ;
            // Clear any data that already exists
            jedis.del(key);
            // Generate several simulated players
            List<String> playerList = new ArrayList<String>();
            for (int i = 0; i < TOTAL_SIZE; ++i)
            
                //Randomly generate an ID for each player
                playerList.add(UUID.randomUUID().toString());
            
            System.out.println("Input all players ");
            // Record the score for each player
            for (int i = 0; i < playerList.size(); i++)
            
                //Randomly generate numbers as the scores of the simulated players
                int score = (int)(Math.random()*5000);
                String member = playerList.get(i);
                System.out.println("Player ID:" + member + ", Player score: " + score);
                //Add the player ID and score to the SortedSet of the corresponding key
                jedis.zadd(key, score, member);
            
            //Print out the ranking of all players
            System.out.println();
            System.out.println(" "+key);
            System.out.println(" All player ranking");
            //Obtain the sorted list of players from the SortedSet of the corresponding key
            Set<Tuple> scoreList = jedis.zrevrangeWithScores(key, 0, -1);
            for (Tuple item : scoreList) {  
                System.out.println("Player ID:"+item.getElement()+", Player score:"+Double.valueOf(item.getScore()).intValue());
              
            // Print out Top 5 players
            System.out.println();
            System.out.println(" "+key);
            System.out.println(" Top players");
            scoreList = jedis.zrevrangeWithScores(key, 0, 4);
            for (Tuple item : scoreList) {  
                System.out.println("Player ID:"+item.getElement()+", Player score:"+Double.valueOf(item.getScore()).intValue());
            
            // Print out a list of specific players
            System.out.println();
            System.out.println(" "+key);
            System.out.println(" players with scores from 1000 to 2000");
            //Obtain a list of players with scores from 1000 to 2000 from the SortedSet of the corresponding key
            scoreList = jedis.zrangeByScoreWithScores(key, 1000, 2000);
            for (Tuple item : scoreList) {  
                System.out.println("Player ID:"+item.getElement()+", Player score:"+Double.valueOf(item.getScore()).intValue());
             
        } catch (Exception e) {
            e.printStackTrace();
        }finally{
            jedis.quit();
            jedis.close();
        
    

```

## Output {#section_j3s_nyv_wdb .section}

After you access the ApsaraDB for Redis instance with the correct address and password and run the above Java code, the following output is displayed:

```
Enter all players 
Player ID: 9193e26f-6a71-4c76-8666-eaf8ee97ac86; score: 3860
Player ID: db03520b-75a3-48e5-850a-071722ff7afb; score: 4853
Player ID: d302d24d-d380-4e15-a4d6-84f71313f27a; score: 2931
Player ID: bee46f9d-4b05-425e-8451-8aa6d48858e6; score: 1796
Player ID: ec24fb9e-366e-4b89-a0d5-0be151a8cad0; score: 2263
玩家ID：e11ecc2c-cd51-4339-8412-c711142ca7aa， 玩家得分: 1848
玩家ID：4c396f67-da7c-4b99-a783-25919d52d756， 玩家得分: 958
玩家ID：a6299dd2-4f38-4528-bb5a-aa2d48a9f94a， 玩家得分: 2428
玩家ID：2e4ec631-1e4e-4ef0-914f-7bf1745f7d65， 玩家得分: 4478
玩家ID：24235a85-85b9-476e-8b96-39f294f57aa7， 玩家得分: 1655
玩家ID：e3e8e1fa-6aac-4a0c-af80-4c4a1e126cd1， 玩家得分: 4064
玩家ID：99bc5b4f-e32a-4295-bc3a-0324887bb77e， 玩家得分: 4852
玩家ID：19e2aa6b-a2d8-4e56-bdf7-8b59f64bd8e0， 玩家得分: 3394
玩家ID：cb62bb24-1318-4af2-9d9b-fbff7280dbec， 玩家得分: 3405
玩家ID：ec0f06da-91ee-447b-b935-7ca935dc7968， 玩家得分: 4391
玩家ID：2c814a6f-3706-4280-9085-5fe5fd56b71c， 玩家得分: 2510
玩家ID：9ee2ed6d-08b8-4e7f-b52c-9adfe1e32dda， 玩家得分: 63
玩家ID：0293b43a-1554-4157-a95b-b78de9edf6dd， 玩家得分: 1008
玩家ID：674bbdd1-2023-46ae-bbe6-dfcd8e372430， 玩家得分: 2265
玩家ID：34574e3e-9cc5-43ed-ba15-9f5405312692， 玩家得分: 3734
              游戏名：奔跑吧，阿里！                    
              全部玩家排行榜                    
玩家ID：db03520b-75a3-48e5-850a-071722ff7afb， 玩家得分:4853
玩家ID：99bc5b4f-e32a-4295-bc3a-0324887bb77e， 玩家得分:4852
玩家ID：2e4ec631-1e4e-4ef0-914f-7bf1745f7d65， 玩家得分:4478
玩家ID：ec0f06da-91ee-447b-b935-7ca935dc7968， 玩家得分:4391
玩家ID：e3e8e1fa-6aac-4a0c-af80-4c4a1e126cd1， 玩家得分:4064
玩家ID：9193e26f-6a71-4c76-8666-eaf8ee97ac86， 玩家得分:3860
玩家ID：34574e3e-9cc5-43ed-ba15-9f5405312692， 玩家得分:3734
玩家ID：cb62bb24-1318-4af2-9d9b-fbff7280dbec， 玩家得分:3405
玩家ID：19e2aa6b-a2d8-4e56-bdf7-8b59f64bd8e0， 玩家得分:3394
玩家ID：d302d24d-d380-4e15-a4d6-84f71313f27a， 玩家得分:2931
玩家ID：2c814a6f-3706-4280-9085-5fe5fd56b71c， 玩家得分:2510
玩家ID：a6299dd2-4f38-4528-bb5a-aa2d48a9f94a， 玩家得分:2428
玩家ID：674bbdd1-2023-46ae-bbe6-dfcd8e372430， 玩家得分:2265
玩家ID：ec24fb9e-366e-4b89-a0d5-0be151a8cad0， 玩家得分:2263
玩家ID：e11ecc2c-cd51-4339-8412-c711142ca7aa， 玩家得分:1848
玩家ID：bee46f9d-4b05-425e-8451-8aa6d48858e6， 玩家得分:1796
玩家ID：24235a85-85b9-476e-8b96-39f294f57aa7， 玩家得分:1655
玩家ID：0293b43a-1554-4157-a95b-b78de9edf6dd， 玩家得分:1008
玩家ID：4c396f67-da7c-4b99-a783-25919d52d756， 玩家得分:958
玩家ID：9ee2ed6d-08b8-4e7f-b52c-9adfe1e32dda， 玩家得分:63
      游戏名：奔跑吧，阿里！                    
         Top 玩家                    
玩家ID：db03520b-75a3-48e5-850a-071722ff7afb， 玩家得分:4853
玩家ID：99bc5b4f-e32a-4295-bc3a-0324887bb77e， 玩家得分:4852
玩家ID：2e4ec631-1e4e-4ef0-914f-7bf1745f7d65， 玩家得分:4478
玩家ID：ec0f06da-91ee-447b-b935-7ca935dc7968， 玩家得分:4391
玩家ID：e3e8e1fa-6aac-4a0c-af80-4c4a1e126cd1， 玩家得分:4064
          游戏名：奔跑吧，阿里！                    
          积分在1000至2000的玩家              
玩家ID：0293b43a-1554-4157-a95b-b78de9edf6dd， 玩家得分:1008
玩家ID：24235a85-85b9-476e-8b96-39f294f57aa7， 玩家得分:1655
玩家ID：bee46f9d-4b05-425e-8451-8aa6d48858e6， 玩家得分:1796
玩家ID：e11ecc2c-cd51-4339-8412-c711142ca7aa， 玩家得分:1848
```

