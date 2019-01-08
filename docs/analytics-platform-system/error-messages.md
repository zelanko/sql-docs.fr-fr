---
title: Messages d’erreur - Parallel Data Warehouse | Microsoft Docs
description: Messages d’erreur Parallel Data Warehouse (PDW) signalent les erreurs et problèmes rencontrent par les composants PDW et peuvent également inclure des erreurs de SQL Server visibles dans PDW. Ces messages d’erreur utilisent une syntaxe cohérente pour présenter des informations. Présentation de cette syntaxe vous permettra d’identifier et corriger les problèmes.
author: mzaman1
manager: craigg
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.openlocfilehash: 3ffc7a097845f4652f56d82c572ecfab868d33f1
ms.sourcegitcommit: 1ab115a906117966c07d89cc2becb1bf690e8c78
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/27/2018
ms.locfileid: "52419200"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Messages d’erreur dans Parallel Data Warehouse

Messages d’erreur Parallel Data Warehouse (PDW) signalent les erreurs et problèmes rencontrent par les composants PDW et peuvent également inclure des erreurs de SQL Server visibles dans PDW. Ces messages d’erreur utilisent une syntaxe cohérente pour présenter des informations. Présentation de cette syntaxe vous permettra d’identifier et corriger les problèmes sur SQL Server PDW.  
  
## <a name="Basics"></a>Principes fondamentaux des messages erreur  
Messages d’erreur retournés suivent la même syntaxe.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Il s’agit de valeurs possibles pour chaque champ :  
  
|Champ|Description|Exemple|  
|---------|---------------|-----------|  
|*Error_Indicator*|Le mot « Erreur » ou tout autre texte d’alerte de l’utilisateur à un problème.|d’erreur|  
|*SQL_State_Code*|Le code d’état SQL, en fonction de la spécification ODBC. Le pilote génère le code d’état SQL approprié à tout moment, qu'il renvoie un message à une application. Le texte « Microsoft » indique la source de l’erreur.|42000|  
|*Driver_Details*|Dépendant du pilote plus d’informations, telles que le type du pilote utilisé.|Pilotes ODBC SQL Server 2008 R2 Parallel Data Warehouse|  
|*QueryID*|Identificateur unique pour la requête. Utilisez cette valeur pour trouver des informations supplémentaires relatives au traitement de la requête. Par exemple, les détails de l’exécution de requête figurent dans la Console d’administration à l’aide de l’ID de requête. Pour plus d’informations, consultez [surveiller l’Appliance à l’aide de la Console d’administration](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Si un QueryID n’est pas applicable, le texte « Interne » est renvoyé à l’utilisateur.|QID2377|  
|*Message_String*|Description explicite de l’erreur ou un problème. Lors du retour d’erreurs de SQL Server, il s’agit du texte du message SQL Server.|Seule l’attribution égale peut apparaître dans la liste set d’une instruction UPDATE.|  
  
Ces exemples de valeurs seraient présentés à l’utilisateur comme suit :  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Présentation des alertes de la Console d’administration](understanding-admin-console-alerts.md)  
  
