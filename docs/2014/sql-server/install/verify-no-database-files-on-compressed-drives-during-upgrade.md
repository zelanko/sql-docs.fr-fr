---
title: Vérifier qu’aucun fichier de base de données ne se trouve sur des lecteurs compressés pendant le processus de mise à niveau | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: database-engine
ms.topic: conceptual
helpviewer_keywords:
- compressed drives [SQL Server]
ms.assetid: 63be6853-c54a-42b2-ae1a-db2175f1d28e
author: mashamsft
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 41c183c72188cccb21838e1e574992bfb723c022
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66091160"
---
# <a name="verify-that-no-database-files-are-on-compressed-drives-during-the-upgrade-process"></a>Vérifier qu'aucun fichier de base de données ne se trouve sur des lecteurs compressés pendant le processus de mise à niveau
  Le Conseiller de mise à niveau a détecté des fichiers de base de données sur un lecteur compressé. 
  [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas créer ni mettre à niveau des bases de données sur des lecteurs compressés.  
  
## <a name="component"></a>Composant  
 [!INCLUDE[ssDE](../../includes/ssde-md.md)]  
  
## <a name="corrective-action"></a>Action corrective  
 Lorsque vous installez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], sélectionnez un lecteur non compressé pour les bases de données système et vérifiez que les bases de données à mettre à niveau ne se trouvent pas sur des lecteurs compressés. Toutefois, sachez que lorsque la base de données a été mise à niveau, vous pouvez placer des bases de données et des groupes de fichiers secondaires en lecture seule sur un système de fichiers compressé NTFS.  
  
## <a name="see-also"></a>Voir aussi  
 [Problèmes de mise à niveau Moteur de base de données](../../../2014/sql-server/install/database-engine-upgrade-issues.md)   
 [Le conseiller de mise à niveau de SQL Server 2014 &#91;nouveau&#93;](sql-server-2014-upgrade-advisor.md)  
  
  
