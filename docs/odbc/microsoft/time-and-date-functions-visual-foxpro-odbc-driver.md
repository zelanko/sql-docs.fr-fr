---
title: Fonctions d’heure et de date (pilote ODBC Visual FoxPro) | Microsoft Docs
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
ms.openlocfilehash: 537af13edf943e27a634d3a8ba4f0f85c645251f
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "67912404"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Fonctions d’heure et de date (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions ODBC de date et d’heure prises en charge par le pilote ODBC Visual FoxPro. Lorsque la grammaire Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, l’équivalent Visual FoxPro est listé.  
  
|Grammaire ODBC|Grammaire de Visual FoxPro|  
|------------------|---------------------------|  
|CAILLÉ *()*|DATE *()*|  
|CURTIME *()*|HEURE *()*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH (*date_exp)*|JOUR *()*|  
|HEURE *(time_exp)*||  
|MINUTE *(time_exp)*||  
|MOIS *(time_exp)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|NOW *()*|DATETIME *()*|  
|DEUXIÈME *(time_exp)*|S *(time_exp)*|  
|SEMAINE *(date_exp)*||  
|ANNÉE *(date_exp)*||  
  
 Les fonctions d’heure et de date suivantes ne sont pas prises en charge :  
  
 DAYOFYEAR *(date_exp)*  
  
 TRIMESTRE *(date_exp)*  
  
 TIMESTAMPADD *(intervalle, integer_exp, timestamp_exp)*  
  
 TIMESTAMPDIFF *(intervalle, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Séquences d’échappement ODBC  
 Le pilote prend également en charge la séquence d’échappement ODBC pour les données de date et d’horodatage. La syntaxe de la clause Escape est la suivante :  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 Dans cette syntaxe, **d** indique que la *valeur* est une date au *format aaaa-mm-jj* et que **TS** indique que la *valeur* est un horodateur au format *aaaa-mm-jj hh : mm : SS*[.* f...*] format. La syntaxe raccourcie pour les données de date et d’horodatage est la suivante :  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Par exemple, chacune des instructions suivantes met à jour la table ALLTYPES à l’aide de la syntaxe abrégée date et timestamp dans une commande SQL UPDATE prise en charge :  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les séquences d’échappement, consultez [séquences d’échappement dans ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) dans le *Guide de référence du programmeur ODBC*.
