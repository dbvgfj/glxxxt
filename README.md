ER图




![](https://cloud.githubusercontent.com/assets/16076941/19418324/330c7a58-93f4-11e6-9e31-c7be1576dc49.png)




# sql脚本
create database equipment ;
use  equipment ;
CREATE TABLE `设备` (
  `设备号` int(11) NOT NULL,
  `设备类型` varchar(45) DEFAULT NULL,
  `保养时间` date DEFAULT NULL,
  PRIMARY KEY (`设备号`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
CREATE TABLE `设备类型` (
  `设备类型ID` int(11) NOT NULL,
  `设备类型名` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`设备类型ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
CREATE TABLE `设备项目` (
  `设备项目ID` int(11) NOT NULL,
  `设备类型ID` int(11) DEFAULT NULL,
  `设备项目名` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`设备项目ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
CREATE TABLE `保养记录` (
  `保养记录ID` int(11) NOT NULL,
  `设备号` int(11) DEFAULT NULL,
  `保养人` varchar(45) DEFAULT NULL,
  `组别` int(11) DEFAULT NULL,
  `保养时间` date DEFAULT NULL,
  `保养内容` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`保养记录ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;
CREATE TABLE `保养消耗` (
  `保养消耗ID` int(11) NOT NULL,
  `保养记录ID` int(11) DEFAULT NULL,
  `原料` varchar(45) DEFAULT NULL,
  `数量` int(11) DEFAULT NULL,
  `单位` varchar(45) DEFAULT NULL,
  PRIMARY KEY (`保养消耗ID`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8;

INSERT INTO `equipment`.`设备`
(`设备号`,
`设备类型`,
`保养时间`)
VALUES
(1,6000V及以上电机,2016-01-02);
INSERT INTO `equipment`.`设备类型`
(`设备类型ID`,
`设备类型名`)
VALUES
(1,6000V及以上电机);
INSERT INTO `equipment`.`设备项目`
(`设备项目ID`,
`设备类型ID`,
`设备项目名`)
VALUES
(1,1,6000V接线盒内瓷瓶、端子);
INSERT INTO `equipment`.`保养记录`
(`保养记录ID`,
`设备号`,
`保养人`,
`组别`,
`保养时间`,
`保养内容`)
VALUES
(1,1,张三,1,2016-01-02,换一个螺丝);
INSERT INTO `equipment`.`保养消耗`
(`保养消耗ID`,
`保养记录ID`,
`原料`,
`数量`,
`单位`)
VALUES
(1,1,螺丝,1,个);

SELECT b.设备号,b.设备类型,b.保养时间 
 FROM 保养记录 AS a,设备 AS b,设备类型 AS c 
 WHERE a.设备号=b.设备号 
 and b.设备类型=c.设备类型名 
 and curdate()-b.保养时间<30

SELECT b.设备号,b.设备类型,c.保养类别,a.保养人,a.组别,a.保养时间,a.保养内容,d.原料,d.数量,d.单位
 FROM 保养记录 AS a,设备 AS b,设备类型 AS c ,保养消耗 AS d
 WHERE a.设备号=b.设备号 
 and b.设备类型=c.设备类型名 
 and a.保养记录ID=d.保养记录ID
 
 
 
 axure交互系统 
 请看这个里面的~
 https://github.com/dbvgfj/dbvgfj.glxxxt
