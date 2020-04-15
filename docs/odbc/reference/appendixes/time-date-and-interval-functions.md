---
title: Fonctions d’heure, de date et d’intervalle Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- functions [ODBC], time functions
- functions [ODBC], date functions
- interval functions [ODBC]
- functions [ODBC], interval functions
- time functions [ODBC]
- date functions [ODBC]
ms.assetid: bdf054a0-7aba-4e99-a34a-799917376fd5
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: aec3d6b23383edcc9659ff884e8cd71b0595dae1
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81302820"
---
# <a name="time-date-and-interval-functions"></a>Fonctions d'heure, de date et d'intervalle
Le tableau suivant répertorie les fonctions d’heure et de date qui sont incluses dans l’ensemble de fonctions scalaires de l’ODBC. Une application peut déterminer quelle fonction d’heure et de date est prise en charge par un conducteur en appelant **SQLGetInfo** avec un *type d’information* de SQL_TIMEDATE_FUNCTIONS.  
  
 Arguments désignés comme *timestamp_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *ODBC-time-escape*, *ODBC-date-escape*, ou *ODBC-timestamp-escape*, où le type de données sous-jacente pourrait être représenté comme SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, SQL_TYPE_DATE, ou SQL_TYPE_TIMESTAMP.  
  
 Les arguments désignés comme *date_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou une *ODBC-date-évasion* ou *ODBC-timestamp-escape*, où le type de données sous-jacente pourrait être représenté comme SQL_CHAR, SQL_VARCHAR, SQL_TYPE_DATE, ou SQL_TYPE_TIMESTAMP.  
  
 Les arguments désignés comme *time_exp* peuvent être le nom d’une colonne, le résultat d’une autre fonction scalaire, ou un *ODBC-time-escape* ou *ODBC-timetamp-escape*, où le type de données sous-jacente pourrait être représenté comme SQL_CHAR, SQL_VARCHAR, SQL_TYPE_TIME, ou SQL_TYPE_TIMESTAMP.  
  
 Les fonctions de CURRENT_DATE, de CURRENT_TIME et de CURRENT_TIMESTAMP échaudées chronométrées ont été ajoutées dans ODBC 3.0 pour s’aligner sur SQL-92.  
  
|Fonction|Description|  
|--------------|-----------------|  
|**CURRENT_DATE) (** (ODBC 3.0)|Retourne la date actuelle.|  
|**CURRENT_TIME[(** précision **temporelle)]** (ODBC 3.0) *time-precision*|Retourne l'heure locale actuelle. *L’argument de précision* temporelle détermine la précision secondes de la valeur retournée.|  
|**CURRENT_TIMESTAMP**<br /> **[(** *timestamp-précision* **)]** (ODBC 3.0)|Retourne la date locale actuelle et l’heure locale comme une valeur timetamp. *L’argument de précision de l’humidité du temps* détermine la précision secondes de l’horloge de retour.|  
|**CURDATE) )** (ODBC 1.0)|Retourne la date actuelle.|  
|**CURTIME) )** (ODBC 1.0)|Retourne l'heure locale actuelle.|  
|**DAYNAME (** *date_exp* **)** (ODBC 2.0)|Retourne une chaîne de caractères contenant le nom spécifique à la source de données de la journée (par exemple, du dimanche au samedi ou du soleil. à sam pour une source de données qui utilise l’anglais, ou Sonntag via Samstag pour une source de données qui utilise l’allemand) pour la partie de jour de *date_exp*.|  
|**DAYOFMONTH(** *date_exp* **)** (ODBC 1.0)|Retourne le jour du mois en fonction du champ du mois en *date_exp* comme une valeur integer dans la gamme de 1-31.|  
|**DAYOFWEEK(** *date_exp* **)** (ODBC 1.0)|Retourne le jour de la semaine en fonction du terrain de la semaine en *date_exp* comme une valeur integer dans la gamme de 1-7, où 1 représente le dimanche.|  
|**DAYOFYEAR(** *date_exp* **)** (ODBC 1.0)|Rendements du jour de l’année en fonction du champ de l’année en *date_exp* comme une valeur integer dans la gamme de 1-366.|  
|**EXTRACT(** *extrait-champ DE* *l’extraction-source* **)** (ODBC 3.0)|Retourne la partie *extrait-champ* de *l’extrait-source*. *L’argument de source d’extrait* est une expression de date ou d’intervalle. *L’argument de champ d’extrait* peut être l’un des mots clés suivants :<br /><br /> ANNÉE MOIS JOUR HEURE MINUTE DEUXIÈME<br /><br /> La précision de la valeur retournée est définie par implémentation. L’échelle est de 0 à moins que SECOND ne soit spécifiée, auquel cas l’échelle n’est pas inférieure à la précision fractionnelle des secondes du champ *d’extraction-source.*|  
|**HEURE (** *time_exp* **)** (ODBC 1.0)|Retourne l’heure en fonction du champ d’heures en *time_exp* comme une valeur integer dans la gamme de 0-23.|  
|**MINUTE (** *time_exp* **)** (ODBC 1.0)|Retourne la minute en fonction du champ minute dans *time_exp* comme une valeur integer dans la gamme de 0-59.|  
|**MONTH (** *date_exp* **)** (ODBC 1.0)|Retourne le mois en fonction du champ du mois en *date_exp* comme une valeur integer dans la gamme de 1-12.|  
|**MONTHNAME (** *date_exp* **)** (ODBC 2.0)|Retourne une chaîne de caractères contenant le nom spécifique à la source de données du mois (par exemple, de janvier à décembre ou de janvier à décembre pour une source de données qui utilise l’anglais, ou Januar par Dezember pour une source de données qui utilise l’allemand) pour la partie mois de *date_exp*.|  
|**MAINTENANT( )** (ODBC 1.0)|Retourne la date et l’heure actuelles comme une valeur timetamp.|  
|**QUARTER (** *date_exp* **)** (ODBC 1.0)|Retourne le trimestre en *date_exp* comme valeur integer dans la gamme de 1-4, où 1 représente Janvier 1 au 31 Mars.|  
|**SECOND (** *time_exp* **)** (ODBC 1.0)|Retourne le deuxième en fonction du deuxième champ en *time_exp* comme une valeur integer dans la gamme de 0-59.|
|**TIMESTAMPADD (** *intervalle*, *integer_exp*, *timestamp_exp* **)** (ODBC 2.0)|Retourne l’ampoule calculée en ajoutant *integer_exp* intervalles de *type* à *timestamp_exp*. Les valeurs valides *d’intervalle* sont les mots clés suivants :<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> où des secondes fractionnées sont exprimées en milliardièmes de seconde. Par exemple, la déclaration suivante de sqL renvoie le nom de chaque employé et sa date d’anniversaire d’un an :<br /><br /> `SELECT NAME, {fn  TIMESTAMPADD(SQL_TSI_YEAR, 1, HIRE_DATE)} FROM  EMPLOYEES`<br /><br /> Si *timestamp_exp* est une valeur temporelle et *l’intervalle* spécifie les jours, les semaines, les mois, les trimestres ou les années, la partie date de *timestamp_exp* est fixée à la date actuelle avant de calculer l’humidité de temps qui en résulte.<br /><br /> Si *timestamp_exp* est une valeur de date et *l’intervalle* spécifie fractionnelle secondes, secondes, minutes ou heures, la partie de temps de *timestamp_exp* est réglée à 0 avant de calculer l’humidité temporelle résultante.<br /><br /> Une application détermine quels intervalles une source de données prend en charge en appelant **SQLGetInfo** avec l’option SQL_TIMEDATE_ADD_INTERVALS.|  
|**TIMESTAMPDIFF (** *intervalle*, *timestamp_exp1*, *timestamp_exp2* **)** (ODBC 2.0)|Retourne le nombre *d’intervalles* de type par lequel *timestamp_exp2* est supérieur *à timestamp_exp1.* Les valeurs valides *d’intervalle* sont les mots clés suivants :<br /><br /> SQL_TSI_FRAC_SECOND<br /><br /> SQL_TSI_SECOND<br /><br /> SQL_TSI_MINUTE<br /><br /> SQL_TSI_HOUR<br /><br /> SQL_TSI_DAY<br /><br /> SQL_TSI_WEEK<br /><br /> SQL_TSI_MONTH<br /><br /> SQL_TSI_QUARTER<br /><br /> SQL_TSI_YEAR<br /><br /> où des secondes fractionnées sont exprimées en milliardièmes de seconde. Par exemple, la déclaration suivante de SQL renvoie le nom de chaque employé et le nombre d’années qu’il a employées :<br /><br /> `SELECT NAME, {fn  TIMESTAMPDIFF(SQL_TSI_YEAR, {fn CURDATE()}, HIRE_DATE)} FROM EMPLOYEES`<br /><br /> Si l’expression de l’un ou l’autre timetamp est une valeur temporelle et *l’intervalle* spécifie les jours, les semaines, les mois, les trimestres ou les années, la partie de date de ce timetamp est fixée à la date actuelle avant de calculer la différence entre les timetamps.<br /><br /> Si l’expression timetamp est une valeur de date et *l’intervalle* spécifie fractionnelle secondes, secondes, minutes ou heures, la partie de temps de ce timetamp est réglée à 0 avant de calculer la différence entre les timetamps.<br /><br /> Une application détermine quels intervalles une source de données prend en charge en appelant **SQLGetInfo** avec l’option SQL_TIMEDATE_DIFF_INTERVALS.|  
|**SEMAINE (** *date_exp* **)** (ODBC 1.0)|Retourne la semaine de l’année en fonction du champ de la semaine en *date_exp* comme une valeur integer dans la gamme de 1-53.|  
|**ANNÉE (** *date_exp* **)** (ODBC 1.0)|Rendements de l’année en fonction du champ de l’année dans *date_exp* comme une valeur integer. La plage est dépendante de la source de données.|
