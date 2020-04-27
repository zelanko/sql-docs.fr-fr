---
title: Propriétés personnalisées de la destination SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 202fd03beea5ec2fbf4b3fc29978ba9e112010df
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62900833"
---
# <a name="sql-server-destination-custom-properties"></a>Propriétés personnalisées de la destination SQL Server
  La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispose à la fois de propriétés personnalisées et des propriétés communes à tous les composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|Boolean|Impose l’utilisation de la valeur de propriété DefaultCodePage. La valeur par défaut de cette propriété est `False`.|  
|BulkInsertCheckConstraints|Boolean|Valeur qui spécifie si l'insertion en bloc vérifie les contraintes. La valeur par défaut de cette propriété est `True`.|  
|BulkInsertFireTriggers|Boolean|Valeur qui spécifie si l'insertion en bloc exécute des déclencheurs dans les tables. La valeur par défaut de cette propriété est `False`.|  
|BulkInsertFirstRow|Integer|Valeur qui spécifie la première ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée|  
|BulkInsertKeepIdentity|Boolean|Valeur qui spécifie si les valeurs peuvent être insérées dans des colonnes d'identité. La valeur par défaut de cette propriété est `False`.|  
|BulkInsertKeepNulls|Boolean|Valeur qui spécifie si l'insertion en bloc conserve les valeurs NULL. La valeur par défaut de cette propriété est `False`.|  
|BulkInsertLastRow|Integer|Valeur qui spécifie la dernière ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.|  
|BulkInsertMaxErrors|Integer|Valeur qui spécifie le nombre d'erreurs au-delà duquel l'insertion en bloc s'arrête. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.|  
|BulkInsertOrder|String|Noms des colonnes de tri. Chaque colonne peut être triée par ordre croissant ou décroissant. En cas d'utilisation de plusieurs colonnes de tri, les noms des colonnes sont séparés par des virgules.|  
|BulkInsertTableName|String|Table ou vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données dans laquelle les données sont copiées.|  
|BulkInsertTablock|Boolean|Valeur qui spécifie si la table est verrouillée lors de l'insertion en bloc. La valeur par défaut de cette propriété est `True`.|  
|DefaultCodePage|Integer|Page de codes à utiliser lorsque les informations de page de codes ne sont pas disponibles à partir de la source de données.|  
|MaxInsertCommitSize|Integer|Valeur qui spécifie le nombre maximal de lignes à insérer dans un lot. Lorsque la valeur est nulle, toutes les lignes sont insérées dans un lot unique.|  
|Délai d'expiration|Integer|Valeur qui spécifie le nombre de secondes pendant lesquelles la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] patiente avant de s'arrêter si aucune donnée disponible ne peut être insérée. Une valeur égale à 0 signifie que la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’expire pas. La valeur par défaut de cette propriété est 30.|  
  
 Les entrées et les colonnes d’entrée de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’ont pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination SQL Server](sql-server-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](../common-properties.md)  
  
  
