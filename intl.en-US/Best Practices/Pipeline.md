# Pipeline {#concept_nl3_r1w_wdb .concept}

## Scenarios {#section_sdc_qbw_wdb .section}

ApsaraDB for Redis provides a pipeline feature similar to that of Redis. A client interacts with a server through one-way pipelines, one for sending requests and the other for receiving responses. You can send operation requests successively from the client to the server; however, the client receives the response to each request from the server until it sends a quit message to the server.      

Pipelines are useful, for example, when several operation commands need to be quickly submitted to the server, but the responses and operation results are not required immediately. In this case, pipelines are used as a batch processing tool to optimize the performance. The performance is enhanced mainly because the overhead of the TCP connection is reduced.    

However, the client using pipelines in the app connects to the server exclusively, and non-pipeline operations are blocked until the pipelines are closed. If you must perform other operations at the same time, you can establish a dedicated connection for pipeline operations to separate them from conventional operations.  

## Sample code 1 {#section_tdc_qbw_wdb .section}

**Performance comparison**

```
package pipeline.kvstore.aliyun.com;
import java.util.Date;
import redis.clients.jedis.Jedis;
Import redis. Clients. Jedis. pipeline;
public class RedisPipelinePerformanceTest {
        static final String host = "xxxxxx.m.cnhza.kvstore.aliyuncs.com";
        static final int port = 6379;
        static final String password = "password";
        public static void main(String[] args) {
            Jedis jedis = new Jedis(host, port);
                //ApsaraDB for Redis  instance password
                String authString = jedis.auth(password);// password
                if (! authString.equals("OK")) {
                    System. Err. println ("auth failed:" + authstring );
                    Jedis. Close ();
                    return;
                }
                //Execute several commands successively
                final int COUNT=5000;
                String key = "KVStore-Tanghan";
                // 1 ---Without using pipeline operations---
                jedis.del(key);//Initializes the key
                Date ts1 = new Date();
                for (int i = 0; i < COUNT; i++) {
                     //Sends a request and receives the response
                    jedis.incr(key);
                }
                Date ts2 = new Date();
                System.out.println("Without Pipeline > value is:"+jedis.get(key)+" > Operating time:" + (ts2.getTime() - ts1.getTime())+ "ms");
                //2 ----Using pipeline operations---
                jedis.del(key);//Initializes the key
                Pipeline p1 = jedis.pipelined();
                Date ts3 = new Date();
                for (int i = 0; i < COUNT; i++) {
                    //Sends the request 
                    p1.incr(key);
                }
                // Receives the response
                p1.sync();
                Date ts4 = new Date();
                 System.out.println("Using Pipeline > value is:"+jedis.get(key)+" > Operating time:" + (ts4.getTime() - ts3.getTime())+ "ms");
                jedis.close();
        }
    }
```

## Output1 {#section_p2c_qbw_wdb .section}

After you access the ApsaraDB for Redis instance with the correct address and password and run the preceding Java code, the following output is displayed. The output shows that the performance is enhanced with pipelines.  

```
Without pipelines > value: 5000 > Time elapsed: 5844 ms
With pipelines > value: 5000 > Time elapsed: 78 ms
```

## Sample code 2 {#section_r2c_qbw_wdb .section}

With pipelines defined in Jedis, responses are processed in two methods, as shown in the following sample code:

```
package pipeline.kvstore.aliyun.com;
import java.util.List;
import redis.clients.jedis.Jedis;
import redis.clients.jedis.Pipeline;
import redis.clients.jedis.Response;
    public class PipelineClientTest {
        Static final string host = "maid ";
        static final int port = 6379;
        static final String password = "password";
        public static void main(String[] args) {
            Jedis jedis = new Jedis(host, port);
                // ApsaraDB for Redis instance password
                String authString = jedis.auth(password);// password
                if (! authString.equals("OK")) {
                    System.err.println("AUTH Failed: " + authString);
                    jedis.close();
                    return;
                }
                String key = "KVStore-Test1";
                jedis.del(key);//Initialization
                // -------- Method 1
                Pipeline p1 = jedis.pipelined();
                System.out.println("-----Method1-----");
                for (int i = 0; i < 5; i++) {
                    p1.incr(key);
                    System.out.println("Pipeline sends requests");
                }
                // After sending all requests, the client starts receiving responses
                System.out.println("Sending requests completed,start to receive response");
                List<Object> responses = p1.syncAndReturnAll();
                if (responses == null || responses.isEmpty()) {
                    jedis.close();
                    throw new RuntimeException("Pipeline error: no respond received");
                }
                for (Object resp : responses) {
                    System.out.println("Pipeline received response: " + resp.toString());
                }
                System.out.println();
                //-------- Method 2
                System.out.println("-----Method2-----");
                jedis.del(key);//Initialization
                Pipeline p2 = jedis.pipelined();  
                //Declare the responses first
                Response<Long> r1 = p2.incr(key); 
                System.out.println("Pipeline sending requests");
                Response<Long> r2 = p2.incr(key);
                System.out.println("Pipeline sending requests");
                Response<Long> r3 = p2.incr(key);
                System.out.println("Pipeline sending requests");
                Response<Long> r4 = p2.incr(key);  
                System.out.println("Pipeline sending requests");
                Response<Long> r5 = p2.incr(key);
                System.out.println("Pipeline sending requests");
                try {  
                     r1.get(); //Errors are generated because the client has not yet started receiving responses
                }catch(Exception e){  
                     System.out.println(" <<<Pipeline error: not start to receive response yet >>> ");    
                }  
              // After sending all requests, the client starts receiving responses
                System.out.println("Sending requests completed, start to receive response");
                p2.sync();  
                System.out.println("Pipeline接收响应Response: " + r1.get());  
                System. Out. println ("pipeline receives response:" + r2.get ());  
                System. Out. println ("pipeline receives response:" + r3.get ());
                System. Out. println ("pipeline receives response:" + r4.get ());
                System. Out. println ("pipeline receives response:" + r5.get ());
                jedis.close();
            }
    }
```

## Output 2 {#section_vfc_qbw_wdb .section}

After you access the ApsaraDB for Redis instance with the correct address and password and run the preceding Java code, the following output is displayed:

```
----- Method 1 -----
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
After sending all requests, the client starts receiving responses
Pipeline receives response 1
Pipeline receives response 2
Pipeline receives response 3
Pipeline receives response 4
Pipeline receives response 5
----- Method 2 -----
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
Pipeline sends a request
<<< Pipeline error: The client has not yet started receiving responses >>>  
After sending all requests, the client starts receiving responses
Pipeline receives response 1
Pipeline receives response 2
Pipeline receives response 3
Pipeline receives response 4
Pipeline receives response 5
```

