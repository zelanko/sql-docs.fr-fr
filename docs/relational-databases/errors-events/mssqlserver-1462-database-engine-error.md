---
title: MSSQLSERVER_1462 | Microsoft Docs
ms.custom: 
ms.date: 04/04/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology: database-engine
ms.tgt_pltfrm: 
ms.topic: language-reference
helpviewer_keywords: 1462 (Database Engine error)
ms.assetid: 680e9c1c-a9d6-4765-b601-956d0a83324c
caps.latest.revision: "12"
author: edmacauley
ms.author: edmaca
manager: cguyer
ms.workload: Inactive
ms.openlocfilehash: 0d3af95b7118a843710f208158d1ad7aa2ce614b
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="mssqlserver1462"></a>MSSQLSERVER_1462
  
## <a name="details"></a>Détails  
  
|||  
|-|-|  
|Nom du produit|SQL Server|  
|ID d'événement|1462|  
|Source de l'événement|MSSQLSERVER|  
|Composant|SQLEngine|  
|Nom symbolique|DBM_DISABLED_DUE_TO_FAILED_REDO|  
|Texte du message|La mise en miroir de bases de données est désactivée en raison de l'échec du rétablissement d'une opération précédente. Impossible de reprendre.|  
  
## <a name="explanation"></a>Explication  
La mise en miroir de bases de données n'a pas pu rétablir un enregistrement de journal sur l'instance miroir.  
  
### <a name="possible-causes"></a>Causes possibles  
La cause la plus probable est qu'une opération d'ajout de fichier a été effectuée sur la base de données principale, mais qu'elle a ensuite échoué sur la base de données miroir car les noms de fichiers ou les structures de répertoires ne sont pas les mêmes sur le serveur principal et le serveur miroir.  
  
## <a name="user-action"></a>Action de l'utilisateur  
Consultez le journal des erreurs [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] pour connaître la cause de cette erreur. Essayez de résoudre le problème et de reprendre la mise en miroir de la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Résoudre des problèmes de configuration de mise en miroir de bases de données &#40;SQL Server&#41;](~/database-engine/database-mirroring/troubleshoot-database-mirroring-configuration-sql-server.md)  
  
