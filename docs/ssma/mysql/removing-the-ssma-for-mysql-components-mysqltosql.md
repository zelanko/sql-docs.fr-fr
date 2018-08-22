---
title: Suppression de SSMA pour MySQL composants (MySQLToSql) | Microsoft Docs
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
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
caps.latest.revision: 10
author: Shamikg
ms.author: Shamikg
manager: craigg
ms.openlocfilehash: adab686126cb608ae32870a9a138720b77d212bf
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40395906"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Suppression des composants SSMA pour MySQL (MySQLToSql)
Lorsque vous avez terminé les bases de données migration de MySQL vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous souhaiterez peut-être désinstaller des composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, si vous désinstallez le pack d’extension à partir de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , puis, SSMA n’est plus prise en charge la migration des données de MySQL vers la base de données cible (SQL Server/SQL Azure) en utilisant le moteur de Migration de données côté serveur.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Désinstallation de SSMA pour MySQL Client  
Vous pouvez désinstaller SSMA à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour MySQL**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du Pack d’Extension  
Vous pouvez supprimer le pack d’extension à l’aide de **Ajout / Suppression de programmes**.  
  
**Pour désinstaller le pack d’extension**  
  
1.  Dans le panneau de configuration, ouvrez **Ajout / Suppression de programmes**.  
  
2.  Sélectionnez **Microsoft SQL Server Migration Assistant pour le Pack d’Extension MySQL**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller le pack d’extension, cliquez sur **Oui**.  
  
4.  Sur les Instances avec la page de Scripts de base de données d’utilitaires, sélectionnez une instance, puis cliquez sur **suivant**.  
  
5.  Dans la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilisera vos informations d’identification Windows pour tenter de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion et mot de passe.  
  
6.  Dans la page opération terminée, cliquez sur **OK**.  
  
7.  Dans la page Terminer, cliquez sur **Exit**.  
  
Une fois le processus de désinstallation est terminé, vous pouvez vérifier que les objets dans le **sysdb.ssma_MySQL** schéma, voire la totalité **sysdb** de base de données, a été supprimée à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]. Toutefois, si vous utilisez d’autres produits SSMA, ils également utilisent le **sysdb** base de données. Si la base de données existe et que vous êtes sûr qu’aucune autre base de données font référence aux objets dans cette base de données, vous pouvez détacher la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour MySQL Client &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installation des composants SSMA sur SQL Server](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
