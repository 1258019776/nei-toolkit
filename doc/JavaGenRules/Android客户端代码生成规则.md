# Android �ͻ��˴����Զ����ɹ���
## һ��Model ���ɹ���
### 1. ���Ͷ�Ӧ��ϵ���������η�

Model �� NEI �е��Զ�����������һһ��Ӧ����ÿһ���Զ�����������ͣ�����Ҫ���ɶ�Ӧ�� Model��ÿ��model���̳���HTBaseModel, �����к��а汾�ŵȹ����ֶΣ�������Ҫ��ÿ��model�����ļ������� `import com.netease.hthttp.model.HTBaseModel;`

���͵Ķ�Ӧ��ϵ�Լ��������η��������£�

| NEI ��������  | Java �������� | ע�� |
| :--- | :--- | :---
| �Զ�������  | ͬ���Զ������� | �������η�ȫ��Ϊprivate�������ṩget��set���� |
| String | String |  | 
| Number | double | ���NEI���������κ͸������͵����� |
| Boolean | boolean | ��������ΪisXXX���͵ģ�get����Ϊ public String isXXX(){ return this.isXXX; } |
| Array | java.util.List | ������Ԫ�ص����ͼ���ΪT����ΪList\<T\>����List\<String\>��List\<Double\>��List\<Boolean\> |
| Variable | Object | ��������ɱ����� |
	
��Ӧ���͵����ɽ�����£�

```java

package com.netease.yanxuan.hthttp.model;
// com.netease.yanxuan �ǰ���
// ���ɵ��ļ�TestModel.java��com/netease/yanxuan/hthttp/model/�ļ�����
// ����hthttp.model���ֿ������û�����

import com.netease.hthttp.model.HTBaseModel;
import java.util.List;

/** ʾ��
{
	  number : 1,
	  isMine : true,
	  string : "hehe",
	  array : ["1","2","3"],
	  variable : {},
	  customModel : {
	  		number : 2,
	  		isRight : false
	  }
  }
 */

public class TestModel extends HTBaseModel {
	// Number��������
    private double number;
    private boolean isMine;
    private String string;
	// �������͵����ݣ���Ҫ�����������ݶ���ģ��
	// �����е�����������number���ͣ���Ӧ��д��Double
	// �����е����������ǲ������ͣ���Ӧ��д��Boolean
    private List<String> array;
    private Object variable;
    // ��Ϊȫ��model�඼������ͬһ���ļ����£����ԾͲ���ʹ��ȫ������
    private InnerModel customModel;

    public double getNumber() {
        return number;
    }

    public boolean isMine() {
        return isMine;
    }

    public String getString() {
        return string;
    }

    public List<String> getArray() {
        return array;
    }

    public Object getVariable() {
        return variable;
    }

    public InnerModel getCustomModel() {
        return customModel;
    }

    public void setNumber(double number) {
        this.number = number;
    }

    public void setIsMine(boolean isMine) {
        this.isMine = isMine;
    }

    public void setString(String string) {
        this.string = string;
    }

    public void setArray(List<String> array) {
        this.array = array;
    }

    public void setVariable(Object variable) {
        this.variable = variable;
    }

    public void setCustomModel(InnerModel customModel) {
        this.customModel = customModel;
    }
}
	
```


#### ö�ٵĴ���

Model �е�ö������ȫ����Ӧ�� `String`

����NEI�ж���ö�����ͣ�

![image](ö������NEI.png)

���ɵ�java���룺

```java

package com.netease.yanxuan.hthttp.model;

public interface DayEnum {
    // ����һ /* NEI�ϵ����� */
    public static final String MONDAY = "monday";

    // ���ڶ�
    public static final String TUESDAY = "tuesday";

    // ������
    public static final String WEDNESDAT = "wednesday";

    // ������
    public static final String THUSDAY = "thusday";

    // ������
    public static final String FRIDAY = "friday";

    // ������
    public static final String SATUSDAY = "satusday";

    // ������
    public static final String SUNDAY = "sunday";
}

```

>ע�⣺ ����ö�����͵���interface��������class��Ҳ����enum


* ö����������������е�ʹ��

![image](ö���������Case.png)


```java

private String day;

public String getDay() {
	return day;
}

public void setDay(String day) {
	this.day = day;
}


```

>���ڶ���ö�����͵ı������������java���붨��ΪString

#### ��֧�ֵ� Case

NEI �����в������ֵ�����(����`Map`��`SparseArray`)��`Date` ���ͣ�����Ҫ���⴦���ֵ�����һ������װ��Ϊһ�� Model; `Date` ���� `Number` ���� `String` ����

### 2. Model ������ɹ���

#### ��������

- ���������� NEI �ϵı���������ͬ
- ����������ѭ������ 1 �ڵĹ���
- �Զ����������������ɵ� Model �������� NEI �ϵ������������ļ��İ���Ĭ��Ϊ${Ӧ�ð���}.hthttp.model������hthttp.model�����û���������
- ���ɵ� Model �ļ���������һ��
- ���ɵ� Model �ļ��ڰ���������ļ���Ŀ¼��

���磺

NEI �ϵ�������Ϊ `Company`, �����ɵ��������� `Company`, �ļ���Ϊ `Company.java`, ����Ϊ`com.netease.yanxuan.hthttp.model`, ���ļ�λ��`com/netease/yanxuan/hthttp/model/Company.java`

#### ע�͹���

- �����Ͷ���ǰ�����jsonʾ��
- ��ÿ������ǰ�����ÿ��������ע�ͣ��� NEI �еĲ��������п�������

## ����HttpTask ���ɹ���

### ��������

+ HttpTask ������ NEI �еĽӿ�������ȡ����NEI�ϵĽӿ�����Ϊ `Login`��������Ϊ `LoginHttpTask`
+ Ĭ�ϰ���Ϊ ${Ӧ�ð���}.hthttp.httptask���ļ�λ�ú�����Ϊ ${Ӧ�ð���ָ����Ŀ¼}/hthttp/httptask������ `hthttp.httptask` �û�������
+ ����ӿ����ֺ������ģ���ʹ�ýӿڵ�ַ�� camelCase ��ʽ
+ Request �������ļ�������һ��


### java�ļ�

get����ʾ����

```java

package com.netease.yanxuan.hthttp.httptask;

import com.alibaba.fastjson.JSONArray;
import com.alibaba.fastjson.JSONObject;
import com.netease.hthttp.BaseHttpStringRequestTask;
import com.netease.volley.Request;
import com.netease.yanxuan.hthttp.model.InnerModel;
import com.netease.yanxuan.hthttp.model.TestModel;

import java.util.List;

public class GetExampleHttpTask extends BaseHttpStringRequestTask {

    public GetExampleHttpTask(double param1,      // ע�ͣ�NEI�ϵı�������   /* number ���͵����� */
                              String param2,      // ע�ͣ�NEI�ϵı�������   /* string ���͵����� */
                              Boolean param3,     // ע�ͣ�NEI�ϵı�������   /* boolean ���͵����� */
                              InnerModel param4,  // ע�ͣ�NEI�ϵı�������   /* �Զ������� ���͵����� */
                              List<String> param5) { // ע�ͣ�NEI�ϵı�������   /* ���� ���͵����� */

        /* ���󷽷����� */
        super(Request.Method.GET);
        /* ��url������Ӳ��� */
        mQueryParamsMap.put("param1", Double.toString(param1));
        mQueryParamsMap.put("param2", param2);
        mQueryParamsMap.put("param3", Boolean.toString(param3));
        mQueryParamsMap.put("param4", JSONObject.toJSONString(param4));
        mQueryParamsMap.put("param5", JSONArray.toJSONString(param5));
    }


    /* ��������url��������url����Ĳ��� */
    /*
    @Override
    public String getUrl() {
        return "/xhr/mobile/getexample.json";
    }
    */

    /* ����url��������ǰ���host��������url����Ĳ��� */
    @Override
    protected String getApi() {
        return "/xhr/mobile/getexample.json";
    }


    @Override
    public Class getModelClass() {
        return TestModel.class;
    }
}

```

˵��

- `BaseHttpStringRequestTask` ��Ĭ�ϻ��࣬�û�������, ��Ҫ��� `import com.netease.hthttp.BaseHttpStringRequestTask;`

- ���û����õ���ȫ·��, `com.netease.yanxuan.http.wzp.BaseWzpRequestTask`������Ҫ�޸�Ϊ `extends BaseWzpRequestTask`; ��� `import com.netease.yanxuan.http.wzp.BaseWzpRequestTask;`

- ���������� ( url �������� header ) ���л�������: `double`��`boolean`, ����
`import com.alibaba.fastjson.JSONObject;`

- ������������url��������header�������������� : `List`, ����?`import com.alibaba.fastjson.JSONArray;`

- �����Զ������ͣ���Ҫ�����Ӧ�İ������� `import com.netease.yanxuan.hthttp.model.TestModel;`

post����ʾ����

```java

package com.netease.yanxuan.hthttp.httptask;

import com.alibaba.fastjson.JSONArray;
import com.alibaba.fastjson.JSONObject;
import com.netease.hthttp.BaseHttpStringRequestTask;
import com.netease.volley.Request;
import com.netease.yanxuan.hthttp.model.InnerModel;
import com.netease.yanxuan.hthttp.model.TestModel;

import java.util.List;

public class PostExampleHttpTask extends BaseHttpStringRequestTask {
    public PostExampleHttpTask(double param1,      // ע�ͣ�NEI�ϵı�������   /* number ���͵����� */
                               String param2,      // ע�ͣ�NEI�ϵı�������   /* string ���͵����� */
                               Boolean param3,     // ע�ͣ�NEI�ϵı�������   /* boolean ���͵����� */
                               InnerModel param4,  // ע�ͣ�NEI�ϵı�������   /* �Զ������� ���͵����� */
                               List<String> param5,// ע�ͣ�NEI�ϵı�������   /* ���� ���͵����� */
                               List<Double> param6) { // ע�ͣ�NEI�ϵı�������   /* ���� ���͵����� */

        super(Request.Method.POST);
        mHeaderMap.put("param1", Double.toString(param1));
        mHeaderMap.put("param2", param2);
        mHeaderMap.put("param3", Boolean.toString(param3));
        mHeaderMap.put("param4", JSONObject.toJSONString(param4));
        mHeaderMap.put("param5", JSONArray.toJSONString(param5));
        mBodyMap.put("param6", param6);
    }

    /* ��������url��������url����Ĳ��� */
    /*
    @Override
    public String getUrl() {
        return "http://${hostname}/xhr/mobile/getexample.json";
    }
    */

    /* ����url��������ǰ���host��������url����Ĳ��� */
    @Override
    protected String getApi() {
        return "/xhr/mobile/postexample.json";
    }

    @Override
    public Class getModelClass() {
        return TestModel.class;
    }
}


```

�ϴ�����ʾ����

```java

package com.netease.yanxuan.hthttp.httptask;

import com.netease.hthttp.HttpMethod;
import com.netease.hthttp.multipart.fileupload.http.BaseFileUploadHttpRequestTask;
import com.netease.yanxuan.hthttp.model.TestModel;

import java.io.File;
import java.util.HashMap;

/* BaseFileUploadHttpRequestTask���û�������
 * ���û����õ���ȫ·����com.netease.yanxuan.http.wzp.BaseWzpRequestTask������Ҫ�޸�Ϊ
  * 1. extends BaseWzpRequestTask
  * 2. ��� import com.netease.yanxuan.http.wzp.BaseWzpRequestTask; */
public class UploadExampleHttpTask extends BaseFileUploadHttpRequestTask {
    public UploadExampleHttpTask(File imageFile) {

        super(HttpMethod.PUT, new HashMap<String, File>(), null);
        mFiles.put("file", imageFile);
        mBodyContentType = "multipart/form-data";

        /* ��Ӧ�ð��� com.netease.yanxuan תΪ COM_NETEASE_YANXUAN */
        mBoundary = "COM_NETEASE_YANXUAN_UPLOAD_IMAGE_BOUNDARY";
        /* "image/" �û������� */
        mFileMinetype = "image/" + getFileType(imageFile);
    }

    /* ��������url��������url����Ĳ��� */
    /*
    @Override
    public String getUrl() {
        return "/xhr/mobile/getexample.json";
    }
    */

    /* ����url��������ǰ���host��������url����Ĳ��� */
    protected String getApi() {
        return "api/v1/image/upload";
    }

    public Class getModelClass() {
        return TestModel.class;
    }
}

```


˵����

+ ����������������Ϊ `${NEI�ӿ���}HttpTask`���ļ���Ϊ `${NEI�ӿ���}HttpTask.java`

+ Ĭ�ϰ���Ϊ `${Ӧ�ð���}.hthttp.httptask`���ļ�·��Ϊ `${Ӧ�ð���ȷ����·��}/hthttp/httptask/`

+ ��ͨ�����Ĭ�ϻ���Ϊ `BaseHttpStringRequestTask `, ��Ҫ������ **`import com.netease.hthttp.BaseHttpStringRequestTask;`**

+ �ļ��ϴ���Ĭ�ϻ���Ϊ `BaseFileUploadHttpRequestTask`, ��Ҫ������ **`import com.netease.hthttp.multipart.fileupload.http.BaseFileUploadHttpRequestTask;`**

+ ����ȫ������Ҫ�����ã������õĻ���Ϊ `com.netease.yanxuan.wzp.BaseWzpHttpTask`������Ҫ�޸Ļ���Ϊ `BaseWzpHttpTask`�����һ�� import : `import com.netease.yanxuan.wzp.BaseWzpHttpTask;`

+ ��� NEI ������Ľӿ� url �ǲ����� host �ģ���ʵ�� `getApi`, ����ʵ�� `getUrl`������ȡ��һ��ֵ�� NEI �ӿڵ� `path` ����

+ ��Ҫ�� url ������Ӳ������򽫲�������� `mQueryParamsMap`, �����������͵�д���μ� **get����ʾ��**

+ ��Ҫ�� header ����Ӳ������򽫲�������� `mHeaderMap`, �����������͵�д���μ� **post����ʾ��**

+ ��Ҫ�� body ����Ӳ������򽫲�������� `mBodyMap`, �����������͵�д���μ� **post����ʾ��**

+ ���󷽷������� super ���캯�������ã��� `super(Request.Method.POST);` ������Ҫ��� `import com.netease.hthttp.HttpMethod;`

+ �������󷽷���Ӧ��java������±�


| ���󷽷�  | java���� |
| :--- | :--- |
| get | Request.Method.GET |
| post | Request.Method.POST |
| head | Request.Method.HEAD |
| delete | Request.Method.DELETE |
| put | Request.Method.PUT |


### ������������

#### Case 1�� NEI �����������ж���������һ����Ӧ�ɱ����ͣ����������ͣ�, ������������뺬�пɱ����͵� NEI ��������ƥ��

ʾ����

![image](�������Case1.png)

���磬������� `JsonObject` �����һ������ `result` ��һ���ɱ����ͣ���ô��ʱ��ֻ��Ҫӳ������ɱ����Ͷ�Ӧ����Ϣ�����Ҹ�����ʾ���ɡ�

������Ϊ��

```java

	public Class getModelClass() {
        return TestModel.class;
    }

```

�����������������ǲ�û����Ӧ��result����

![image](�������Case1-null.png)

```java

	public Class getModelClass() {
        return null;
    }

```

#### Case 2�� NEI �����������ж���������һ����Ӧ�ɱ����ͣ��������ͣ�, ������������뺬�пɱ����͵� NEI ��������ƥ��
ʾ����

![image](�������Case2.png)

���磬������� `JsonObject` �����һ������ `result` ��һ���������ͣ���ô��ʱ��ֻ��Ҫӳ��������������е�Ԫ�ض�Ӧ����Ϣ�����Ҹ�����ʾ���ɡ�

������Ϊ��

```java

	/* ע�Ⲣ����List.class */
	public Class getModelClass() {
        return TestModel.class;
    }

```

#### Case 3�� NEI ������������һ��(������)�����������������֮ǰ��code��message��result�ṹ��������������������������ݽ��ж�Ӧ


`Address` ʾ����

![image](�������Case3.jpg)

��ͼ���������� `Address` �������� `province` �� `city`, �����е���������� `Address` �Ķ���ƥ��. ��ôʵ���ļ��Ľ��Ϊ��

������Ϊ��

```java

	public Class getModelClass() {
        return Address.class;
    }

```


`String` ʾ����

![image](�������Case4.png)

��ͼ����������Ϊ `String`. ��ôʵ���ļ��Ľ��Ϊ��

������Ϊ��

```java

	public Class getModelClass() {
        return String.class;
    }

```

`Number` ʾ����

![image](�������Case5.png)

��ͼ����������Ϊ `Number`. ��ôʵ���ļ��Ľ��Ϊ��

������Ϊ��

```java

	public Class getModelClass() {
        return Double.class;
    }

```

`Boolean` ʾ����

![image](�������Case6.png)

��ͼ����������Ϊ `Boolean`. ��ôʵ���ļ��Ľ��Ϊ��

������Ϊ��

```java

	public Class getModelClass() {
        return Boolean.class;
    }

```


��ͼ�������û�з�������

![image](�������Case3-null.png)


```java

	public Class getModelClass() {
        return null;
    }

```

#### Case 3�� NEI ��������������һ������Ϊ�������ͣ�������������뷵�������Ԫ�ؽ��ж�Ӧ

`List<Address>` ʾ����

![image](�������Case7.png)

��ͼ���������� `Address` �������� `province` �� `city`, �����е���������� `Address` �Ķ���ƥ��. ��ôʵ���ļ��Ľ��Ϊ��

������Ϊ��

```java

	public Class getModelClass() {
        return Address.class;
    }

```

���� `List<Boolean>`, `List<Double>`, `List<String>`����