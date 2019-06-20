---
title: Fonctions d’heure et Date (pilote ODBC de Visual FoxPro) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: cf8e7552faf9567dab25ee3dc5b7b293034faef0
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62632769"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Fonctions d’heure et de date (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions de date et heure ODBC pris en charge par le pilote ODBC Visual FoxPro ; lors de la grammaire de Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, le Visual FoxPro équivalent est répertorié.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|CURDATE *( )*|DATE *( )*|  
|CURTIME *( )*|TIME *( )*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH(*date_exp)*|JOUR *)*|  
|HOUR *(time_exp)*||  
|MINUTE *(time_exp)*||  
|MONTH *(time_exp)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|NOW *( )*|DATETIME *( )*|  
|SECOND *(time_exp)*|SEC *(time_exp)*|  
|WEEK *(date_exp)*||  
|YEAR *(date_exp)*||  
  
 Les fonctions de date et heure suivantes ne sont pas prises en charge :  
  
 DAYOFYEAR *(date_exp)*  
  
 QUARTER *(date_exp)*  
  
 TIMESTAMPADD *(intervalle, integer_exp, exp_estampille)*  
  
 TIMESTAMPDIFF *(intervalle, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Séquences d’échappement ODBC  
 Le pilote prend également en charge la séquence d’échappement ODBC pour les données de date et d’horodatage. La syntaxe de clause d’échappement est comme suit :  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 Dans cette syntaxe, **d** indique que *valeur* est une date dans le *aaaa-mm-jj* format et **ts** indique que *valeur*  est un horodateur dans le *aaaa-mm-jj hh : mm :* [.*f...* ] format. La syntaxe raccourcie pour les données de date et l’horodatage est comme suit :  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Par exemple, chacune des instructions suivantes met à jour la table ALLTYPES à l’aide de la syntaxe sténo date et l’horodatage dans une commande de mise à jour de SQL pris en charge :  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les séquences d’échappement, consultez [les séquences d’échappement dans ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) dans le *de référence du programmeur ODBC*.
