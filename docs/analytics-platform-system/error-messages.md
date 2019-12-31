---
title: messages d'erreur
description: Les messages d’erreur des Data Warehouse parallèles signalent les erreurs et les problèmes rencontrés par les composants PDW et peuvent également inclure des erreurs de SQL Server dans les PDW. Ces messages d’erreur utilisent une syntaxe cohérente pour présenter des informations. La compréhension de cette syntaxe vous permettra d’identifier et de corriger les problèmes.
author: mzaman1
ms.prod: sql
ms.technology: data-warehouse
ms.topic: conceptual
ms.date: 04/17/2018
ms.author: murshedz
ms.reviewer: martinle
ms.custom: seo-dt-2019
ms.openlocfilehash: 2d89e80a89df53e85ef8d2bf53c369d9e4dc0d49
ms.sourcegitcommit: d587a141351e59782c31229bccaa0bff2e869580
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74401164"
---
# <a name="error-messages-in-parallel-data-warehouse"></a>Messages d’erreur en parallèle Data Warehouse

Les messages d’erreur des Data Warehouse parallèles signalent les erreurs et les problèmes rencontrés par les composants PDW et peuvent également inclure des erreurs de SQL Server dans les PDW. Ces messages d’erreur utilisent une syntaxe cohérente pour présenter des informations. La compréhension de cette syntaxe vous permettra d’identifier et de corriger les problèmes sur SQL Server PDW.  
  
## <a name="Basics"></a>Notions de base des messages d’erreur  
Les messages d’erreur retournés suivent la même syntaxe.  
  
`Error_Indicator [SQL_State_Code] [Driver_Details] [QueryID] Message_String`  
  
Il s’agit des valeurs possibles pour chaque champ :  
  
|Champ|Description|Exemple|  
|---------|---------------|-----------|  
|*Error_Indicator*|Le mot « erreur » ou un autre texte qui alerte l’utilisateur en cas de problème.|ERROR|  
|*SQL_State_Code*|Code d’état SQL, conformément à la spécification ODBC. Le pilote génère le code d’état SQL approprié chaque fois qu’il retourne un message à une application. Le texte « Microsoft » indique la source de l’erreur.|42000|  
|*Driver_Details*|Détails dépendants du pilote, tels que le type de pilote utilisé.|Pilote de Data Warehouse parallèle ODBC SQL Server 2008 R2|  
|*QueryID*|Identificateur unique de la requête. Utilisez cette valeur pour trouver des informations supplémentaires relatives au traitement de la requête. Par exemple, les détails de l’exécution de la requête se trouvent dans la console d’administration à l’aide de l’ID de requête. Pour plus d’informations, consultez [surveiller l’appliance à l’aide de la console d’administration](monitor-the-appliance-by-using-the-admin-console.md).<br /><br />Si un QueryID n’est pas applicable, le texte « Internal » est renvoyé à l’utilisateur.|QID2377|  
|*Message_String*|Description explicite de l’erreur ou du problème. Lors du renvoi des erreurs SQL Server, il s’agit du texte du message SQL Server.|Seule une attribution égale peut apparaître dans la liste de définition d’une instruction UPDATE.|  
  
Ces exemples de valeurs sont présentés à l’utilisateur comme suit :  
  
`ERROR [42000] [Microsoft][ODBC SQL Server 2008 R2 Parallel Data Warehouse driver][QID2380]Only equal assignment can appear in the set list of an UPDATE statement.`  
  
## <a name="see-also"></a>Voir aussi  
<!-- MISSING LINKS 
[Common Metadata Query Examples &#40;SQL Server PDW&#41;](../sqlpdw/common-metadata-query-examples-sql-server-pdw.md)  
-->
[Fonctionnement des alertes de la console d’administration](understanding-admin-console-alerts.md)  
  
