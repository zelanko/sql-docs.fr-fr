---
title: Niveaux de conformité SQL (ODBC Driver pour Oracle) Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- conformance levels [ODBC], SQL
- SQL conformance levels [ODBC]
- ODBC driver for Oracle [ODBC], conformance levels
ms.assetid: 077a6c6a-2c57-42c9-a4fd-4cf0e65cf7e2
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: e283bbc13f0d0dda055b047b027f7b9816502df5
ms.sourcegitcommit: ce94c2ad7a50945481172782c270b5b0206e61de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81300679"
---
# <a name="sql-conformance-levels-odbc-driver-for-oracle"></a>Niveaux de conformité de SQL (pilote ODBC pour Oracle)
> [!IMPORTANT]  
>  Cette fonctionnalité sera supprimée dans une future version de Windows. Évitez d'utiliser cette fonctionnalité dans de nouveaux travaux de développement, et prévoyez de modifier les applications qui utilisent actuellement cette fonctionnalité. Utilisez plutôt le pilote ODBC fourni par Oracle.  
  
 Le pilote ODBC pour Oracle prend en charge la grammaire SqL Minimum et la grammaire Core SQL et prend également en charge les extensions ODBC suivantes à SQL :  
  
-   Dates, heures et données de timetamp  
  
-   Jointures extérieures gauche et droite  
  
-   Fonctions numériques :  
  
    |||||  
    |-|-|-|-|  
    |Abs|Journal|round|tan|  
    |Ceiling|Log10|second|truncate|  
    |Cos|Mod|sign||  
    |Exp|Pi|sin||  
    |Floor|Power|sqrt||  
  
-   Fonctions de date :  
  
    |||||  
    |-|-|-|-|  
    |Curdate (Curdate)|Dayofweek|nom de mois|second|  
    |Curtime Curtime|Jour de l'année|minute|week|  
    |Nom de jour|Heure|now|year|  
    |Jourofmonth|Month|quarter||  
  
-   Fonctions de chaînes :  
  
    |||||  
    |-|-|-|-|  
    |ASCII|Gauche|droite|ucase|  
    |Char|Longueur|rtrim rtrim||  
    |Concat|Ltrim Ltrim|Soundex||  
    |Lcase|Replace|substring||  
  
-   Fonction de conversion de type :  
  
    ||  
    |-|  
    |Convertir|  
  
-   Fonctions du système :  
  
    ||  
    |-|  
    |Ifnull (En)|  
    |Utilisateur|
