---
title: Activer ou désactiver la collecte de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dbe-cross-instance
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- data collector [SQL Server], disabling
- data collector [SQL Server], enabling
ms.assetid: 0137971b-fb48-4a3e-822a-3df2b9bb09d7
caps.latest.revision: 17
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 78c5da946475869e8207f673d72afcd16f1f0546
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36051288"
---
# <a name="enable-or-disable-data-collection"></a>Activer ou désactiver la collecte de données
  Cette rubrique explique comment activer ou désactiver la collecte de données dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour activer ou désactiver la collecte de données, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Permissions  
 Nécessite l’appartenance au rôle de base de données fixe **dc_admin** ou **dc_operator** (avec l’autorisation EXECUTE) pour exécuter cette procédure.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-enable-the-data-collector"></a>Pour activer le collecteur de données  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** .  
  
2.  Cliquez avec le bouton droit sur **Collecte de données**, puis cliquez sur **Activer la collecte de données**.  
  
#### <a name="to-disable-the-data-collector"></a>Pour désactiver le collecteur de données  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** .  
  
2.  Cliquez avec le bouton droit sur **Collecte de données**, puis sélectionnez **Désactiver la collecte de données**.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-enable-the-data-collector"></a>Pour activer le collecteur de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_enable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-enable-collector-transact-sql) pour activer le collecteur de données.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_enable_collector ;  
```  
  
#### <a name="to-disable-the-data-collector"></a>Pour désactiver le collecteur de données  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_disable_collector](/sql/relational-databases/system-stored-procedures/sp-syscollector-disable-collector-transact-sql) pour désactiver le collecteur de données.  
  
```tsql  
USE msdb;  
GO  
EXEC dbo.sp_syscollector_disable_collector;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Collecte de données](data-collection.md)   
 [Procédures stockées système &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/system-stored-procedures-transact-sql)  
  
  
