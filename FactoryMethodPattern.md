###工厂模式

###概念
工厂方法或者类生成对象，而不是在代码中直接new对象

###好处
如果你想要更改所实例化的类名等，则只需更改该工厂方法内容即可，不需逐一寻找代码中具体实例化的地方（new处）修改了。
为系统结构提供灵活的动态扩展机制，减少了耦合

###使用场景
* 做支付接口的时候，未来可能对应不同的支付网关：支付宝、财付通、网银在线等。
方便未来扩展,设计成工厂模式。定一个专门生产网关接口的工厂，抽象出来,
做成接口形式，让所有的子类都要实现它的接口。
以后加一个支付方式，要使用哪一种支付方式，改变一下参数即可。

* 系统对接多个不同类型的数据库，mysql，oracle，sqlserver

###实现
<pre>
<code>
class Factory
{

    static public function createDb($type = '')
    {
        if ($type == 'mysql') {
            return new dbmysql();
        } elseif ($type == 'sqlite') {
            return new dbsqlite();
        } else {//报错
            throw new Exception("Error db type", 1);
        }
    }
}

$db = Factory::createDb('mysql');
$db = Factory::createDb('sqlite');
$db->conn();
</code>
</pre>