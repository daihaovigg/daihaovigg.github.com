目前在安卓开发中使用的fastjson，据说，阿里巴巴FastJson是一个Json处理工具包，包括“序列化”和“反序列化”两部分，它具备如下特征：
速度最快，测试表明，fastjson具有极快的性能，超越任其他的Java Json parser。包括自称最快的JackJson；功能强大，完全支持Java Bean、集合、Map、日期、Enum，支持范型，支持自省；无依赖，能够直接运行在Java SE 5.0以上版本；支持Android；开源 (Apache 2.0)。

#### 加入jar包 
在安卓工程中使用gradle自动依赖fastjson：在build.gradle文件中的dependencies中加入compile 'com.alibaba:fastjson:1.2.7'，具体版本可以查看maven仓库，然后sync即可在项目中使用fastjson。

### 使用
在工程中import com.alibaba.fastjson.JSON;即可使用。
序列化：JSON.toJSONString(data)即可序列化为String

反序列化：
1.JSON.parseObject(data, new TypeReference<>(){})即可反序列化为你所需的类型。
2.也可以直接使用JSON.parseObject(data，obj.class)
3.直接使用parse，
`Map<String, String> res = (Map<String, String>) JSON.parse(data) `
4.解析{'':'','':[{},{}]}形如这样的json，可以：
` obj = JSON.parseObject(data);`
` a = obj.getString("a");`
` JSONArray b = obj.getJSONArray("b");`  
再对JSONArray使用b.get(i)来获取每条json，再解析即可。


