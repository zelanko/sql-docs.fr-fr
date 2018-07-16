---
title: Annuler l’inscription d’un serveur cible dans un serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- SQL Server Agent jobs, target servers
- target servers [SQL Server], defecting
- SQL Server Agent jobs, master servers
- master servers [SQL Server], defecting target servers
- defecting target servers
ms.assetid: a6da262b-7b38-4ce4-bfd6-6a557c6e8a84
caps.latest.revision: 29
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 35f113cfd0e038940c00b710b31f254da6343805
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37305039"
---
# <a name="defect-a-target-server-from-a-master-server"></a>Annuler l'inscription d'un serveur cible dans un serveur maître
  Cette rubrique décrit comment désinscrire un serveur cible d'un serveur maître dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)], de [!INCLUDE[tsql](../../includes/tsql-md.md)] ou d'objets SMO (SQL Server Management Objects). Exécutez cette procédure à partir du serveur cible.  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour annuler l'inscription d'un serveur cible à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
     [SMO](#PowerShellProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Pour exécuter cette procédure stockée, l'utilisateur doit être membre du rôle de serveur fixe `sysadmin`.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Pour annuler l'inscription d'un serveur cible dans un serveur maître  
  
1.  Dans l' **Explorateur d'objets**, développez un serveur qui est configuré comme serveur cible.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Désinscrire**.  
  
3.  Cliquez sur **Oui** pour confirmer que vous voulez désinscrire ce serveur cible d'un serveur maître.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-defect-a-target-server-from-a-master-server"></a>Pour annuler l'inscription d'un serveur cible dans un serveur maître  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
```  
sp_msx_defect ;  
```  
  
 Pour plus d’informations, consultez [sp_msx_defect &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-defect-transact-sql).  
  
##  <a name="PowerShellProcedure"></a> À l’aide de SQL Server Management Objects (SMO)  
 Utilisez la méthode `MsxDefect Method`.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un environnement multi-serveur](create-a-multiserver-environment.md)   
 [Administration automatisée à l'échelle d'une entreprise](automated-administration-across-an-enterprise.md)   
 [Annuler l’inscription de plusieurs serveurs cibles dans un serveur maître](defect-multiple-target-servers-from-a-master-server.md)  
  
  
