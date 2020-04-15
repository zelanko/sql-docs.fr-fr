---
title: Fonctions d’heure et de date (Visual FoxPro ODBC Driver) Microsoft Docs
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
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 86260f8e7245bed15122d4dbfc4649131674e17f
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81303060"
---
# <a name="time-and-date-functions-visual-foxpro-odbc-driver"></a>Fonctions d’heure et de date (pilote ODBC Visual FoxPro)
Le tableau suivant répertorie les fonctions d’heure et de date de l’ODBC prises en charge par le Visual FoxPro ODBC Driver; lorsque la grammaire Visual FoxPro pour la même fonction diffère de la syntaxe ODBC, l’équivalent Visual FoxPro est répertorié.  
  
|Grammaire ODBC|Grammaire visuelle FoxPro|  
|------------------|---------------------------|  
|CURDATE *( )*|Date *( )*|  
|CURTIME *( )*|TEMPS *( )*|  
|DAYNAME *(date_exp)*|CDOW *(date_exp)*|  
|DAYOFMONTH *(date_exp)*|JOUR *( )*|  
|HEURE *(time_exp)*||  
|MINUTE *(time_exp)*||  
|MONTH *(time_exp)*||  
|MONTHNAME *(date_exp)*|CMONTH *(date_exp)*|  
|MAINTENANT *( )*|DATETIME *( )*|  
|SECOND *(time_exp)*|SEC *(time_exp)*|  
|SEMAINE *(date_exp)*||  
|ANNÉE *(date_exp)*||  
  
 Les fonctions d’heure et de date suivantes ne sont pas prises en charge :  
  
 JOUROFYEAR *(date_exp)*  
  
 QUARTER *(date_exp)*  
  
 TIMESTAMPADD *(intervalle, integer_exp, timestamp_exp)*  
  
 TIMESTAMPDIFF *(intervalle, timestamp_exp1, timestamp_exp2)*  
  
## <a name="odbc-escape-sequences"></a>Séquences d’échappement ODBC  
 Le conducteur prend également en charge la séquence d’évacuation de l’ODBC pour les données sur les dates et les heures de travail. La syntaxe de clause d’évasion est la suivante :  
  
```  
--(*vendor(Microsoft),product(ODBC) d 'value' *)-  
--(*vendor(Microsoft),product(ODBC) ts ''value' *)-  
```  
  
 Dans cette syntaxe, **d** indique que la *valeur* est une date dans le format *yyyy-mm-dd* et **ts** indique que la *valeur* est un temps humide dans le *yyyy-mm-dd hh:mm:ss*[.* f...*] Format. La syntaxe abrégé pour les données sur les dates et les heures est la suivante :  
  
```  
{d 'value'}  
{ts 'value'}  
```  
  
 Par exemple, chacune des déclarations suivantes met à jour le tableau ALLTYPES en utilisant la syntaxe shorthand date et l’humidité du temps dans une commande SQL UPDATE supportée :  
  
```  
UPDATE alltypes  
   SET DAT_COL={d'1968-04-28'}  
   WHERE KEY=111  
  
UPDATE alltypes  
   SET DTI_COL={ts'1968-04-28 12:00:00'}  
   WHERE KEY=111  
```  
  
## <a name="remarks"></a>Notes  
 Pour plus d’informations sur les séquences d’évasion, voir [Escape Sequences in ODBC](../../odbc/reference/develop-app/escape-sequences-in-odbc.md) dans la *référence du programmeur ODBC*.
