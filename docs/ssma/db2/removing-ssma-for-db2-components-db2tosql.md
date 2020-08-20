---
description: Suppression de SSMA pour les composants DB2 (DB2ToSQL)
title: Suppression de SSMA pour les composants DB2 (DB2ToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: 4ee0d698-6246-48eb-b963-d62be81cab6a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 0341869ff5d39ad35fce6ac450d293eaac1feb38
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88488167"
---
# <a name="removing-ssma-for-db2-components-db2tosql"></a>Suppression de SSMA pour les composants DB2 (DB2ToSQL)
Une fois que vous avez terminé la migration des bases de données de DB2 vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous souhaiterez peut-être désinstaller les composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, vous ne devez pas désinstaller le pack d’extension de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si vos bases de données migrées n’utilisent plus de fonctions dans le schéma **ssma_DB2** de la base de données **sysdb** .  
  
## <a name="uninstalling-the-ssma-for-db2-client"></a>Désinstallation du client SSMA pour DB2  
Vous pouvez désinstaller SSMA à l’aide d' **Ajout/suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.  
  
2.  Sélectionnez ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Migration pour DB2**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du pack d’extension  
Si vous êtes sûr que vos bases de données migrées n’utilisent pas d’objets dans le schéma **sysdb. ssma_DB2** , vous pouvez supprimer le pack d’extension en le supprimant du schéma-il n’y a pas de désinstallation de Windows  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour le client DB2 &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-for-db2-client-db2tosql.md)  
[Installation des composants SSMA sur SQL Server &#40;DB2ToSQL&#41;](../../ssma/db2/installing-ssma-components-on-sql-server-db2tosql.md)  
  
