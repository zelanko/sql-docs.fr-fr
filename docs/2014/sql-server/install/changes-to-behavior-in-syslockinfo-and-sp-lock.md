---
title: Modifie le comportement dans syslockinfo et sp_lock | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- database-engine
ms.topic: conceptual
helpviewer_keywords:
- syslockinfo
- sp_lock
ms.assetid: b9892ae3-ac15-48be-8b52-78dbed6467ed
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: a6dfe3901cb23cff65dd96fa084232310ef91ede
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48104569"
---
# <a name="changes-to-behavior-in-syslockinfo-and-splock"></a>Modifications du comportement dans syslockinfo et sp_lock
  **syslockinfo** et **sp_lock** peuvent retourner des valeurs inattendues. Ils peuvent également retourner des lignes supplémentaires, alors que les versions antérieures de **syslockinfo** et de **sp_lock** retournaient un maximum de deux lignes par ressource de verrou.  
  
 L'accès à des informations à partir de **syslockinfo** et l'exécution de **sp_lock** requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="description"></a>Description  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], le **rsc_objid** et **rsc_indid** colonnes dans **syslockinfo** et **objid** et **indid**  colonnes dans **sp_lock** retournent toujours l’objet ID et ID d’index. Dans [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], la valeur 0 peut être renvoyée.  
  
 Dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)], **syslockinfo** et **sp_lock** retournent un maximum de deux lignes pour n’importe quelle ressource de verrou donnée dans une transaction unique. À partir de [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)], lorsque le partitionnement de verrous est activé, plusieurs lignes peuvent être renvoyées pour la même ressource s'exécutant sous une transaction. Il peuvent être jusqu'à N + 1 lignes retourné, où N est le nombre d’unités centrales. En outre, il est maintenant possible d'afficher des demandes GRANTED et WAITING pour la même ressource, alors que cela n'était pas possible dans [!INCLUDE[ssVersion2000](../../includes/ssversion2000-md.md)].  
  
## <a name="permissions"></a>Permissions  
 requièrent l'autorisation VIEW SERVER STATE sur le serveur.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau du moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](/sql/2014/sql-server/install/sql-server-2014-upgrade-advisor)  
  
  
