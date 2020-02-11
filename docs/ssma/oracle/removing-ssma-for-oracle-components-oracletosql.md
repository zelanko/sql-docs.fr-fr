---
title: Suppression de SSMA pour les composants Oracle (OracleToSQL) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling the Extension Pack
ms.assetid: 8b527a56-4e52-487a-9ac9-2320388e6d7d
author: Shamikg
ms.author: Shamikg
manager: shamikg
ms.openlocfilehash: 0434f88c46d14672c84f5f7939488a827b229e27
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "68266562"
---
# <a name="removing-ssma--for-oracle-components-oracletosql"></a>Suppression de composants SSMA pour Oracle (OracleToSQL)
Une fois que vous avez terminé la migration des bases [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de données d’Oracle vers, vous pouvez désinstaller les composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, vous ne devez pas désinstaller le Pack [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] d’extension de, sauf si vos bases de données migrées n’utilisent plus de fonctions dans le schéma **ssma_oracle** de la base de données **sysdb** .  
  
## <a name="uninstalling-the-ssma-for-oracle-client"></a>Désinstallation du client SSMA pour Oracle  
Vous pouvez désinstaller SSMA à l’aide d' **Ajout/suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.  
  
2.  ** [!INCLUDE[msCoName](../../includes/msconame_md.md)] Sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Assistant Migration pour Oracle**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du pack d’extension  
Si vous êtes sûr que vos bases de données migrées n’utilisent pas d’objets dans le schéma **sysdb. ssma_oracle** , vous pouvez supprimer le pack d’extension en utilisant **Ajout/suppression de programmes**.  
  
**Pour désinstaller le pack d’extension**  
  
1.  Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.  
  
2.  Sélectionnez **Assistant Migration Microsoft SQL Server pour le pack d’extension Oracle**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller le pack d’extension, cliquez sur **Oui**.  
  
4.  Sur la page instances avec scripts de base de données utilitaires, sélectionnez une instance, puis cliquez sur **suivant**.  
  
5.  Sur la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour essayer de se connecter à l’instance [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]de. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] un nom de connexion et un mot de passe.  
  
6.  Dans la page opération terminée, cliquez sur **OK**.  
  
7.  Dans la page terminer, cliquez sur **quitter**.  
  
Après la désinstallation, vous pouvez vérifier que les objets du schéma **sysdb. ssma_oracle** , et éventuellement la base de données **sysdb** entière, ont été [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]supprimés à l’aide de. Toutefois, si vous utilisez d’autres produits SSMA, ils utilisent également la base de données **sysdb** . Si la base de données existe et que vous êtes sûr qu’aucune autre base de données ne référence des objets de cette base de données, vous pouvez détacher la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour Oracle client &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-for-oracle-client-oracletosql.md)  
[Installation des composants SSMA sur SQL Server &#40;OracleToSQL&#41;](../../ssma/oracle/installing-ssma-components-on-sql-server-oracletosql.md)  
  
