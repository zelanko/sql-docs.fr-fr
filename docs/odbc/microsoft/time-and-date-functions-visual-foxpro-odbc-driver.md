---
title: "Fonctions d’heure et Date (le pilote ODBC Visual FoxPro) | Documents Microsoft"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- drivers
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ODBC date functions [ODBC]
- Visual FoxPro ODBC driver [ODBC], time and date functions
- FoxPro ODBC driver [ODBC], time and date functions
- time and date functions [ODBC]
- ODBC time and date functions [ODBC]
- date functions [ODBC]
ms.assetid: c1fb63b7-af50-45d6-8dec-ae6ea7119527
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f7e6274d77a9cdd4de6cbcaef559ca99f77b3608
ms.openlocfilehash: bab52b29d54416dca84d18cb0cd2b832da1b4d63
ms.contentlocale: fr-fr
ms.lasthandoff: 09/09/2017

---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Fonctions d’heure et Date (le pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions de date et heure ODBC pris en charge par le pilote ODBC Visual FoxPro ; lors de la grammaire Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, le Visual FoxPro équivalent est répertorié.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|CURDATE*)*|DATE*)*|  
|CURTIME*)*|TEMPS*)*|  
|HEUREDAYNAME*(date_exp)*|CDOW*(date_exp)*|  
|DAYOFMONTH (*date_exp)*|JOUR*)*|  
|HEURE*(time_exp)*||  
|MINUTE*(time_exp)*||  
|MOIS*(time_exp)*||  
|MONTHNAME*(date_exp)*|CMONTH*(date_exp)*|  
|MAINTENANT*)*|DATETIME*)*|  
|DEUXIÈME*(time_exp)*|S*(time_exp)*|  
|SEMAINE*(date_exp)*||  
|ANNÉE*(date_exp)*||  
  
 Les fonctions de date et heure suivantes ne sont pas prises en charge :  
  
 DAYOFYEAR *(date_exp)*  
  
 TRIMESTRE *(date_exp)*  
  
 TIMESTAMPADD *(intervalle, integer_exp, exp_estampille)*  
  
 TIMESTAMPDIFF *(intervalle, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Séquences d’échappement ODBC  
 Le pilote prend également en charge la séquence d’échappement ODBC pour les données de date et l’horodatage. La syntaxe de la clause d’échappement est comme suit :  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)—  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)—  
```  
  
 Dans cette syntaxe, **d** indique que *valeur* est une date dans le *aaaa-mm-jj* format et **ts** indique que *valeur* est un horodateur dans le *aaaa-mm-jj hh : mm :*[.* f... *] format. La syntaxe raccourcie pour les données de date et l’horodatage est la suivante :  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Par exemple, chacune des instructions suivantes met à jour la table ALLTYPES à l’aide de la syntaxe abrégée de date et l’horodatage dans une commande de mise à jour de SQL pris en charge :  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les séquences d’échappement, consultez [les séquences d’échappement dans ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) dans les *de référence du programmeur ODBC*.
