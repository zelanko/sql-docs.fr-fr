---
title: SQLTables (pilote dBASE) | Documents Microsoft
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: odbc
ms.reviewer: ''
ms.suite: sql
ms.technology:
- drivers
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- DBase driver [ODBC], SQLTables
- SQLTables function [ODBC], dBASE Driver
ms.assetid: 45938efb-b678-47d8-9345-644fa26ad679
caps.latest.revision: 6
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 4c31c0995c6516c68cebb7fb0e2ec374c36923f2
ms.sourcegitcommit: 7a6df3fd5bea9282ecdeffa94d13ea1da6def80a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2018
---
# <a name="sqltables-dbase-driver"></a>SQLTables (pilote dBASE)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote de dBASE. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous [référence de l’API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* a la valeur NULL, car aucun des pilotes prend en charge les noms de propriétaire. Avec *szTableOwner* la valeur NULL, toutes les tables sont retournées. NULL est retourné dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un répertoire.|  
|*SzTableType*|Pour les fichiers dBASE, « TABLE » est le seul type de table pris en charge.|
