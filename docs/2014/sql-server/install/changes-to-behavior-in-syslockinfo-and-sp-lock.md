---
title: Modifications du comportement dans syslockinfo et sp_lock | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: e8c6534449ffc4e89efcd49c943726bf6ecd9f26
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "66096646"
---
# <a name="changes-to-behavior-in-syslockinfo-and-sp_lock"></a>Modifications du comportement dans syslockinfo et sp_lock
  **syslockinfo** et **sp_lock** peuvent retourner des valeurs inattendues. Ils peuvent également retourner des lignes supplémentaires, alors que les versions antérieures de **syslockinfo** et de **sp_lock** retournaient un maximum de deux lignes par ressource de verrou.  
  
 L'accès à des informations à partir de **syslockinfo** et l'exécution de **sp_lock** requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], les colonnes **rsc_objid** et **rsc_indid** dans **syslockinfo** et les colonnes **objid** et **indid** dans **sp_lock** retournent toujours l'ID d'objet et l'ID d'index. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], la valeur 0 peut être renvoyée.  
  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** et **sp_lock** retournent un maximum de deux lignes pour toute ressource de verrou donnée dans une même transaction. À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], lorsque le partitionnement de verrous est activé, plusieurs lignes peuvent être renvoyées pour la même ressource s'exécutant sous une transaction. Il peut y avoir jusqu’à N + 1 lignes, où N est le nombre de processeurs. En outre, il est maintenant possible d'afficher des demandes GRANTED et WAITING pour la même ressource, alors que cela n'était pas possible dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="permissions"></a>Autorisations  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
