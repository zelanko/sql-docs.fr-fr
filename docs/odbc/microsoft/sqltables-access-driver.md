---
description: SQLTables (pilote Access)
title: SQLTables (pilote Access) | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.prod_service: connectivity
ms.reviewer: ''
ms.technology: connectivity
ms.topic: conceptual
helpviewer_keywords:
- SQLTables function [ODBC], Access Driver
- Access driver [ODBC], SQLTables
ms.assetid: 94423cf9-341a-4db6-bb10-8f5448df7fc3
author: David-Engel
ms.author: v-daenge
ms.openlocfilehash: 69dce4116064cdb7509f628fcc493e57c414666e
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88339915"
---
# <a name="sqltables-access-driver"></a>SQLTables (pilote Access)
> [!NOTE]  
>  Cette rubrique fournit des informations spécifiques au pilote d’accès. Pour obtenir des informations générales sur cette fonction, consultez la rubrique appropriée sous référence de l' [API ODBC](../../odbc/reference/syntax/odbc-api-reference.md).  
  
|Argument|Commentaires|  
|--------------|--------------|  
|*szTableOwner*|Le seul argument valide pour *szTableOwner* est null, car aucun des pilotes ne prend en charge les noms de propriétaire. Si *szTableOwner* a la valeur null, toutes les tables sont retournées. La valeur NULL est retournée dans la colonne TABLE_OWNER.|  
|*szTableQualifier*|Dans la colonne TABLE_QUALIFIER, **SQLTables** retourne le chemin d’accès à un fichier de base de données.|  
|*SzTableType*|Lorsque le pilote Microsoft Access est utilisé, la « TABLE système » est prise en charge pour *szTableType* pour les tables système, « synonyme » est pris en charge pour les tables attachées et « View » est pris en charge pour les requêtes qui retournent des lignes.|  
  
## <a name="see-also"></a>Voir aussi  
 [Fonction SQLTables](../../odbc/reference/syntax/sqltables-function.md)
