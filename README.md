![CLEVER DATA GIT REPO](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/0-clever-data-github.png "李聪明的数据库")

# 使用DBCC Open Tran（'MyDB'）查找所有数据库的开放交易（Open Transactions）
#### Find Open Transactions Across All Databases Using DBCC OpenTran(‘MyDB’)
**发布-日期:2014年4月9日（评论）**

![#](images/##############?raw=true "#")

## Contents

- [中文](#中文)
- [English](#English)
- [SQL Logic](#Logic)
- [Build Info](#Build-Info)
- [Author](#Author)
- [License](#License) 


## 中文
这是一个可以查看任何数据库中是否存在任何开放交易（open transaction）的快速脚本。 当然，有很多方法可以查看此活动，但这个方法可能有助于之后构建的内容。

## English
Here’s a quick script you can run to see if there are any open transactions across any of your databases. Sure; there are a number of ways to see this activity, but this might be helpful for something to build on later.

---
## Logic
```SQL
use master;
set nocount on
declare @check_for_open_transactions varchar(max)
set @check_for_open_transactions = ”
select @check_for_open_transactions = @check_for_open_transactions +
‘
dbcc opentran(”’ + name + ”’); ‘ + char(10)
from sys.databases where name not in (‘master’, ‘model’, ‘tempdb’, ‘msdb’)
order by database_id asc
exec (@check_for_open_transactions)


```
只需浏览结果即可。 你可以很容易看到交易。

Just browse the results. You’ll see the transactions readily.


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

- **李聪明的数据库 Lee's Clever Data**
- **Mike的数据库宝典 Mikes Database Collection**
- **李聪明的数据库** "Lee Songming"

[![Gist](https://img.shields.io/badge/Gist-李聪明的数据库-<COLOR>.svg)](https://gist.github.com/congmingshuju)
[![Twitter](https://img.shields.io/badge/Twitter-mike的数据库宝典-<COLOR>.svg)](https://twitter.com/mikesdatawork?lang=en)
[![Wordpress](https://img.shields.io/badge/Wordpress-mike的数据库宝典-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

---
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Lee Songming](https://raw.githubusercontent.com/LiCongMingDeShujuku/git-resources/master/1-clever-data-github.png "李聪明的数据库")

