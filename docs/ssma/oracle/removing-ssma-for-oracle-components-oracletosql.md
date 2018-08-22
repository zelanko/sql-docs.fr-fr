---
title: Suppression de SSMA pour les composants Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.technology: ssma
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
caps.latest.revision: 6
author: Shamikg
ms.author: Shamikg
manager: v-thobro
ms.openlocfilehash: a301770224db68e0f812650ce87c15a3f2e5f7bf
ms.sourcegitcommit: 603d2e588ac7b36060fa0cc9c8621ff2a6c0fcc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/14/2018
ms.locfileid: "40395881"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Suppression de composants SSMA pour Oracle (OracleToSQL)
Lorsque vous avez terminé les bases de données migration d’Oracle vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous souhaiterez peut-être désinstaller des composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, vous ne devez pas désinstaller le pack d’extension à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sauf si vos bases de données migrées ne plus utilisent les fonctions dans le **ssma_oracle** schéma de la **sysdb** base de données.  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Désinstallation de SSMA pour Oracle Client  
Vous pouvez désinstaller SSMA à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez  **[!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Migration Assistant pour Oracle**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du Pack d’Extension  
Si vous êtes sûr vos bases de données migrées n’utilisent pas les objets dans le **sysdb.ssma_oracle** schéma, vous pouvez supprimer le pack d’extension à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller le pack d’extension**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour le Pack d’Extension Oracle**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller le pack d’extension, cliquez sur **Oui**.  
  
4.  Sur les Instances avec la page de Scripts de base de données d’utilitaires, sélectionnez une instance, puis cliquez sur **suivant**.  
  
5.  Dans la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilisera vos informations d’identification Windows pour tenter de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion et mot de passe.  
  
6.  Dans la page opération terminée, cliquez sur **OK**.  
  
7.  Dans la page Terminer, cliquez sur **Exit**.  
  
Après la désinstallation, vous pouvez vérifier que les objets dans le **sysdb.ssma_oracle** schéma, voire la totalité **sysdb** de base de données, a été supprimée à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Toutefois, si vous utilisez d’autres produits SSMA, ils également utilisent le **sysdb** base de données. Si la base de données existe et que vous êtes sûr qu’aucune autre base de données ne référence des objets dans cette base de données, vous pouvez détacher la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle Client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
