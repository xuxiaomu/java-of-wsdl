java����wsdl�ӿ�

ǰ�᣺�� �Ѿ��ṩ��һ��wsdl�ӿڢ� �ýӿ�����������
�����Ϊ���ַ�ʽ��
1.ʹ��cxf��wsdl2java�������ɱ����ࣨʹ�÷�ʽ���Ǳ������ʹ�ã��� 
2.����Զ�̵�web service����������client��Զ�̵��ýӿڡ�
��Ϊ�ڶ��ַ�ʽ����Ҫ��Ϥwsdl��û�����˽ⲻ̫�ò�������Ҫ˵�µ�һ�ַ�ʽ��

ʹ��cxf��wsdl2java�������ɱ�������Ҫ�������£�
1����װJDK������jdk�汾��1.6�Ļ��������ᱨ��jdk6���ֻ֧��ws2.1�淶�汾��
2������apache-cxf������������CXF��http://cxf.apache.org/download.html Ŀǰ���°汾Ϊ3.1.7����ѹ������������CXF_HOME�������%CXF_HOME %/bin��path����������
3��CMD����������wsdl2java -help����������ʾ˵�������Ѿ���ȷ���á� 
4��CMD�������� �� wsdl2java -encoding utf-8 -d D:\javalib\web http://m.zsjsjy.com/services/resource?wsdl 
��wsdl ��·����
-encoding��ʾ���ɵ�Java�ļ������ʽΪutf8��-d��ʾ��������·��ΪD:\javalib\we�����к������������ĵ�ǰ·�������Թ�ʹ�õ��� 
5�������ɵ��ർ����Ŀ��һ����񶼽�XXXService������������Ϊ���ĵĽӿ��ļ�

 
���������е����������⣺
1��
��Ϊjdk��1.6�汾�ģ��������ص�apache-cxf��������ѹ��ʹ�ñ�������cxf��jdk��jar���г�ͻ����ģ�
���������ϰ汾��apache-cxf-2.6.12.zip ������һЩ���ϣ�����������Ű�jdk������1.7��
��������� ����jdk1.7�ļ����µ�jre�µ�lib�ļ��´���һ��endorsed�ļ��У�D:\java\jdk1.7.0_16\jre\lib\endorsed����
��apache-cxf��jaxb��Ӧ������2.2jar�����Ƶ�endorsed�У����ɹ���������java�ࡣ
2��
�ɹ�����java�ļ�������Ŀ�󣬵�����java�б���İ��ļ������serviece���л����й��캯������ע��˵��Ҫjaxws2.2���������ɲſɡ�
����������˵�䲻����������ͨ��������jax-ws2.2��Լ��java6��ͻ�� �������ֲ��ܽ���java5�����룬����Ҫ����jax-ws��Լ�汾��
����취��ִ����� wsdl2java -frontend jaxws21 -d D:\javalib\cn http://m.zsjsjy.com/services/resource?wsdl 
���������������
3��
�ӿڵ��ò���ʱ����Exception in thread "main" org.apache.cxf.service.factory.ServiceConstructionException
ԭ�������ɽӿ�java�࣬namespace·������ԭ��Ĭ�ϵģ����ҷŽ���Ŀʱ���·���Ѿ������ڵ��ˡ�����취��
��Ҫ �Զ���-p·�� �������ɣ�
 wsdl2java -frontend jaxws21 -encoding utf-8 -p cn.teacheredu.app.projectconfigcenter.proj.module.screen.tlogin.zswebservice -d D:\javalib\cn http://m.zsjsjy.com/services/resource?wsdl  
 