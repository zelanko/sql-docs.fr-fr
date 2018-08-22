---
title: Suppression de SSMA pour DB2 composants (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
applies_to:
- Azure SQL Database
- SQL Server
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: 6f93ca145c96e2cc9b6d86e0ebc8c2c9899afad9
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395471"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Suppression de SSMA pour DB2 composants (DB2ToSQL)
Lorsque vous avez terminé migration bases de données de DB2 vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous souhaiterez peut-être désinstaller des composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, vous ne devez pas désinstaller le pack d’extension à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si vos bases de données migrées ne plus utilisent les fonctions dans le **ssma_DB2** schéma de la **sysdb** base de données.  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Désinstallation de SSMA pour DB2 Client  
Vous pouvez désinstaller SSMA à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’Assistant de Migration pour DB2**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du Pack d’Extension  
Si vous êtes sûr vos bases de données migrées n’utilisent pas les objets dans le **sysdb.ssma_DB2** schéma, vous pouvez supprimer le pack d’extension en le supprimant du schéma : il n’y a aucune désinstallation de Windows  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour DB2 Client &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Installation des composants SSMA sur SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
