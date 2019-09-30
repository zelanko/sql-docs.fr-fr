---
title: Propriétés personnalisées de la destination SQL Server | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
ms.prod: sql
ms.prod_service: integration-services
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: b736aa6d-c154-44a0-be08-f25733fca1d9
author: chugugrace
ms.author: chugu
ms.openlocfilehash: dd60d40c612df33b46ea7394d3bf9b1e53e24df6
ms.sourcegitcommit: e8af8cfc0bb51f62a4f0fa794c784f1aed006c71
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71291777"
---
# <a name="sql-server-destination-custom-properties"></a>Propriétés personnalisées de la destination SQL Server

[!INCLUDE[ssis-appliesto](../../includes/ssis-appliesto-ssvrpluslinux-asdb-asdw-xxx.md)]


  La destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a à la fois des propriétés personnalisées et des propriétés communes à tous les composants de flux de données.  
  
 Le tableau suivant décrit les propriétés personnalisées de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Toutes les propriétés sont en lecture/écriture.  
  
|Nom de la propriété|Type de données|Description|  
|-------------------|---------------|-----------------|  
|AlwaysUseDefaultCodePage|Booléen|Impose l’utilisation de la valeur de propriété DefaultCodePage. La valeur par défaut de cette propriété est **False**.|  
|BulkInsertCheckConstraints|Booléen|Valeur qui spécifie si l'insertion en bloc vérifie les contraintes. La valeur par défaut de cette propriété est **True**.|  
|BulkInsertFireTriggers|Booléen|Valeur qui spécifie si l'insertion en bloc exécute des déclencheurs dans les tables. La valeur par défaut de cette propriété est **False**.|  
|BulkInsertFirstRow|Entier|Valeur qui spécifie la première ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée|  
|BulkInsertKeepIdentity|Booléen|Valeur qui spécifie si les valeurs peuvent être insérées dans des colonnes d'identité. La valeur par défaut de cette propriété est **False**.|  
|BulkInsertKeepNulls|Booléen|Valeur qui spécifie si l'insertion en bloc conserve les valeurs NULL. La valeur par défaut de cette propriété est **False**.|  
|BulkInsertLastRow|Entier|Valeur qui spécifie la dernière ligne à insérer. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.|  
|BulkInsertMaxErrors|Entier|Valeur qui spécifie le nombre d'erreurs au-delà duquel l'insertion en bloc s'arrête. La valeur par défaut de cette propriété est **-1**, ce qui signifie qu’aucune valeur n’a été attribuée.|  
|BulkInsertOrder|String|Noms des colonnes de tri. Chaque colonne peut être triée par ordre croissant ou décroissant. En cas d'utilisation de plusieurs colonnes de tri, les noms des colonnes sont séparés par des virgules.|  
|BulkInsertTableName|String|Table ou vue [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dans la base de données dans laquelle les données sont copiées.|  
|BulkInsertTablock|Booléen|Valeur qui spécifie si la table est verrouillée lors de l'insertion en bloc. La valeur par défaut de cette propriété est **True**.|  
|DefaultCodePage|Entier|Page de codes à utiliser lorsque les informations de page de codes ne sont pas disponibles à partir de la source de données.|  
|MaxInsertCommitSize|Entier|Valeur qui spécifie le nombre maximal de lignes à insérer dans un lot. Lorsque la valeur est nulle, toutes les lignes sont insérées dans un lot unique.|  
|Délai d'expiration|Entier|Valeur qui spécifie le nombre de secondes pendant lesquelles la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] patiente avant de s'arrêter si aucune donnée disponible ne peut être insérée. Une valeur égale à 0 signifie que la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’expire pas. La valeur par défaut de cette propriété est 30.|  
  
 Les entrées et les colonnes d’entrée de la destination [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n’ont pas de propriétés personnalisées.  
  
 Pour plus d’informations, consultez [Destination SQL Server](../../integration-services/data-flow/sql-server-destination.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Propriétés communes](https://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
  
