![MIKES DATA WORK GIT REPO](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_01.png "Mikes Data Work")        

# Get SQL Server Versions And Their Corresponding Patche Needed With SQL
**Post Date: July 10, 2015**        



## Contents    
- [About Process](##About-Process)  
- [SQL Logic](#SQL-Logic)  
- [Build Info](#Build-Info)  
- [Author](#Author)  
- [License](#License)       

## About-Process

<p>Here's some SQL logic that will show you the SQL Server Version and will list the Patches the servers need if you're behind on your versioning. Works up to SQL Server 2014.</p>      


## SQL-Logic
```SQL
use master;
 
set nocount on
 
select
 
'SQL Version' = right(left(@@version, 25), 15)
 
, 'Service Pack' = serverproperty('productlevel')
 
, 'R2?' =
 
case
 
when serverproperty('productversion') between '10.50.0000.0' and '10.51.0000.0' then ' R2'
 
else ''
 
end
 
, 'Current' =
 
case
 
when serverproperty('productversion') between '9.0.1399.06' and '9.0.4036' then 'Requires SQL 2005 SP4'
 
when serverproperty('productversion') between '10.0.1600.21' and '10.0.5500.1' then 'Requires SQL 2008 SP4'
 
when serverproperty('productversion') between '10.50.1600.0' and '10.50.4000.1' then 'Requires SQL 2008 R2 SP3'
 
when serverproperty('productversion') between '11.0.2100.59' and '11.0.3000.1' then 'Requires SQL 2012 SP2'
 
when serverproperty('productversion') between '12.0.2000.7' and '11.0.3000.0' then 'Requires SQL 2012 SP2'
 
else
 
'Current'
 
end
 
, 'Build Number' = serverproperty('productversion')
```
Results will look like this when applied to multiple servers.

![Find SQL Versions And Patches]( https://mikesdatawork.files.wordpress.com/2015/07/image0013.jpg "Get Version And Patch Info With SQL")
 


[![WorksEveryTime](https://forthebadge.com/images/badges/60-percent-of-the-time-works-every-time.svg)](https://shitday.de/)

## Build-Info

| Build Quality | Build History |
|--|--|
|<table><tr><td>[![Build-Status](https://ci.appveyor.com/api/projects/status/pjxh5g91jpbh7t84?svg?style=flat-square)](#)</td></tr><tr><td>[![Coverage](https://coveralls.io/repos/github/tygerbytes/ResourceFitness/badge.svg?style=flat-square)](#)</td></tr><tr><td>[![Nuget](https://img.shields.io/nuget/v/TW.Resfit.Core.svg?style=flat-square)](#)</td></tr></table>|<table><tr><td>[![Build history](https://buildstats.info/appveyor/chart/tygerbytes/resourcefitness)](#)</td></tr></table>|

## Author

[![Gist](https://img.shields.io/badge/Gist-MikesDataWork-<COLOR>.svg)](https://gist.github.com/mikesdatawork)
[![Twitter](https://img.shields.io/badge/Twitter-MikesDataWork-<COLOR>.svg)](https://twitter.com/mikesdatawork)
[![Wordpress](https://img.shields.io/badge/Wordpress-MikesDataWork-<COLOR>.svg)](https://mikesdatawork.wordpress.com/)

 
## License
[![LicenseCCSA](https://img.shields.io/badge/License-CreativeCommonsSA-<COLOR>.svg)](https://creativecommons.org/share-your-work/licensing-types-examples/)

![Mikes Data Work](https://raw.githubusercontent.com/mikesdatawork/images/master/git_mikes_data_work_banner_02.png "Mikes Data Work")

