---
title: Suppression de SSMA pour Sybase (SybaseToSQL) les composants | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2017
ms.prod: sql
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
ms.assetid: aec09593-17d9-4ec2-ac56-3cd8851406fd
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: b3cebc9bb82778390716212fd3b5ae1bf800d3d3
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62667930"
---
# <a name="removing-ssma-for-sybase-components-sybasetosql"></a>Suppression de composants SSMA pour Sybase (SybaseToSQL)
Lorsque vous avez terminé les bases de données migration à partir de Sybase Adaptive Server Enterprise (ASE) à [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous souhaiterez peut-être désinstaller des composants SSMA. Vous pouvez désinstaller les composants du client à tout moment, mais vous ne devez pas désinstaller le pack d’extension à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si vous êtes sûr que vos bases de données migrées ne plus utilisent les fonctions dans le **ssma_syb** schéma de la **sysdb** base de données.  
  
## <a name="uninstalling-the-ssma-for-sybase-client"></a>Désinstallation de SSMA pour Sybase Client  
Vous pouvez désinstaller SSMA à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour Sybase**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du Pack d’Extension  
Si vous êtes sûr vos bases de données migrées n’utilisent pas les objets dans le **sysdb.ssma_syb** schéma, vous pouvez supprimer le pack d’extension à l’aide de **Ajout / Suppression de programmes**.  
  
Pour désinstaller le pack d’extension  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour Sybase Extension Pack**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller le pack d’extension, cliquez sur **Oui**.  
  
4.  Sur les Instances avec la page de Scripts de base de données d’utilitaires, cliquez sur **suivant**.  
  
5.  Dans la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour tenter de se connecter à l’instance de SQL Server. Si vous sélectionnez l’authentification SQL Server, vous devez entrer un nom de connexion SQL Server et le mot de passe.  
  
6.  Dans la page opération terminée, cliquez sur **OK**.  
  
7.  Dans la page Terminer, cliquez sur **Exit**.  
  
Après la désinstallation, vous pouvez vérifier que le **sysdb.ssma_syb** schéma, voire la totalité **sysdb** de base de données, a été supprimée à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Toutefois, si vous utilisez d’autres produits SSMA, ils également utilisent le **sysdb** base de données. Si la base de données existe et que vous êtes sûr qu’aucune autre base de données ne référence des objets dans cette base de données, vous pouvez détacher la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Sybase Client &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-for-sybase-client-sybasetosql.md)  
[Installation des composants SSMA sur SQL Server &#40;SybaseToSQL&#41;](../../ssma/sybase/installing-ssma-components-on-sql-server-sybasetosql.md)  
  
