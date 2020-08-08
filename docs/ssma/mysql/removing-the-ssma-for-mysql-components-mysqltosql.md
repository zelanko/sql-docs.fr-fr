---
title: Suppression des composants SSMA pour MySQL (MySQLToSql) | Microsoft Docs
ms.prod: sql
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.technology: ssma
ms.topic: conceptual
helpviewer_keywords:
- Uninstalling, Extension pack
- Uninstalling, SSMA for MySQL client
ms.assetid: 87cdbd49-a0c9-4b00-8a93-34188b18d11a
author: nahk-ivanov
ms.author: alexiva
ms.openlocfilehash: 27c1ab67a6d62bceb31bb036978f65b3494e4f19
ms.sourcegitcommit: e8f6c51d4702c0046aec1394109bc0503ca182f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2020
ms.locfileid: "87935238"
---
# <a name="removing-the-ssma-for-mysql-components-mysqltosql"></a>Suppression des composants SSMA pour MySQL (MySQLToSql)
Une fois que vous avez terminé la migration des bases de données de MySQL vers [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous pouvez désinstaller les composants SSMA. Vous pouvez désinstaller les composants du client à tout moment. Toutefois, si vous désinstallez le pack d’extension de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , SSMA ne prend plus en charge la migration des données de MySQL vers la base de données cible (SQL Server/SQL Azure) à l’aide du moteur de migration de données côté serveur.  
  
## <a name="uninstalling-the-ssma-for-mysql-client"></a>Désinstallation du client SSMA pour MySQL  
Vous pouvez désinstaller SSMA à l’aide d' **Ajout/suppression de programmes**.  
  
**Pour désinstaller SSMA**  
  
1.  Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.  
  
2.  Sélectionnez **Assistant Migration Microsoft SQL Server pour MySQL**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller SSMA, cliquez sur **Oui**.  
  
## <a name="uninstalling-the-extension-pack"></a>Désinstallation du pack d’extension  
Vous pouvez supprimer le pack d’extension en utilisant **Ajout/suppression de programmes**.  
  
**Pour désinstaller le pack d’extension**  
  
1.  Dans le Panneau de configuration, ouvrez **Ajout/Suppression de programmes**.  
  
2.  Sélectionnez **Assistant Migration Microsoft SQL Server pour MySQL extension Pack**, puis cliquez sur **supprimer**.  
  
3.  Pour confirmer que vous souhaitez désinstaller le pack d’extension, cliquez sur **Oui**.  
  
4.  Sur la page instances avec scripts de base de données utilitaires, sélectionnez une instance, puis cliquez sur **suivant**.  
  
5.  Sur la page Paramètres de connexion, sélectionnez la méthode d’authentification, puis cliquez sur **suivant**.  
  
    L’authentification Windows utilise vos informations d’identification Windows pour essayer de se connecter à l’instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] . Si vous sélectionnez [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] l’authentification, vous devez entrer un [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nom de connexion et un mot de passe.  
  
6.  Dans la page opération terminée, cliquez sur **OK**.  
  
7.  Dans la page terminer, cliquez sur **quitter**.  
  
Une fois le processus de désinstallation terminé, vous pouvez vérifier que les objets du schéma **sysdb. ssma_MySQL** , et éventuellement la base de données **sysdb** entière, ont été supprimés à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] . Toutefois, si vous utilisez d’autres produits SSMA, ils utilisent également la base de données **sysdb** . Si la base de données existe et que vous êtes sûr qu’aucune autre base de données ne fait référence aux objets de cette base de données, vous pouvez détacher la base de données.  
  
## <a name="see-also"></a>Voir aussi  
[Installation de SSMA pour MySQL client &#40;MySQLToSQL&#41;](../../ssma/mysql/installing-ssma-for-mysql-client-mysqltosql.md)  
[Installation des composants SSMA sur SQL Server](installing-ssma-components-on-sql-server-mysqltosql.md)  
  
