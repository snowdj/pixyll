---
published: true
layout: post
category: Econometrics
tags:
  - SAS
  - Panel data
---
## A New Post

glmselect is used to generate design matrix with one hot of categorical variables.

/*
 *
 * 任务代码由 SAS Studio 3.7 生成
 *
 * 生成时间: “18/10/6 下午2:28” 
 * 生成人员: “jonduan0” 
 * 生成服务器: “ODAWS04.ODA.SAS.COM” 
 * 生成 SAS 平台: “Linux LIN X64 3.10.0-693.21.1.el7.x86_64” 
 * 生成 SAS 版本: “9.04.01M5P09132017” 
 * 生成浏览器: “Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/69.0.3497.100 Safari/537.36” 
 * 生成 Web 客户端: “https://odamid.oda.sas.com/SASStudio/main?locale=zh_CN&zone=GMT-07%253A00” 
 *
 */

ods noproctitle;
ods graphics / imagemap=on;

proc sort data=SASHELP.BASEBALL out=Work.preProcessedData;
	by Name YrMajor;
run;

ods exclude all;

proc glmselect data=Work.preProcessedData 
		outdesign(addinputvars)=Work.ets_design;
	class League / param=glm;
	model CrHits=nAssts nError logSalary nHome CrAtBat League /selection=none;
run;

ods exclude none;

proc panel data=WORK.ets_design;
	id Name YrMajor;
	class League;
	model CrHits=&_GLSMOD / fixone;
run;

proc delete data=Work.preProcessedData;
run;

proc delete data=Work.ets_design;
run;
