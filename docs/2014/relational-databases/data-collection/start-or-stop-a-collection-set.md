---
title: Démarrer ou arrêter un jeu d’éléments de collecte | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: supportability
ms.topic: conceptual
helpviewer_keywords:
- collection sets [SQL Server], stopping
- collection sets [SQL Server], starting
ms.assetid: 48a7b2fe-6bc3-4278-a7ec-1babc1290345
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 96f5a873e8d172254e1ea18abbd0c570b27a35ed
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62918441"
---
# <a name="start-or-stop-a-collection-set"></a>Démarrer ou arrêter un jeu d'éléments de collecte
  Cette rubrique explique comment démarrer ou arrêter un jeu d'éléments de collecte dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Limitations et restrictions](#Restrictions)  
  
     [Prérequis](#Prerequisites)  
  
     [Recommandations](#Recommendations)  
  
     [Sécurité](#Security)  
  
-   **Pour démarrer ou arrêter un jeu d'éléments de collecte, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Restrictions"></a> Limitations et restrictions  
  
-   Les procédures stockées et les affichages catalogue du collecteur de données sont stockés dans la base de données **msdb** .  
  
-   Contrairement aux procédures stockées standard, les procédures stockées du collecteur de données utilisent des paramètres de type strict qui ne prennent pas en charge la conversion automatique de type de données. Si ces paramètres ne sont pas appelés à l'aide des types de données appropriés pour les paramètres d'entrée tels qu'ils sont spécifiés dans la description de l'argument, la procédure stockée retourne une erreur.  
  
###  <a name="Prerequisites"></a> Conditions préalables  
  
-   L'Agent SQL Server doit être démarré.  
  
###  <a name="Recommendations"></a> Recommandations  
  
-   Pour obtenir des informations sur les jeux d’éléments de collecte, interrogez l’affichage catalogue [syscollector_collection_sets](/sql/relational-databases/system-catalog-views/syscollector-collection-sets-transact-sql) .  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 Nécessite l’appartenance au rôle de base de données fixe **dc_operator** . Si le jeu d'éléments de collecte n'a pas de compte proxy, l'appartenance au rôle serveur fixe **sysadmin** est requise. Exemples  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-start-a-collection-set"></a>Pour démarrer un jeu d'éléments de collecte  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** et développez **Collecte de données**, puis **Jeux d'éléments de collecte de données système**.  
  
2.  Cliquez avec le bouton droit sur le jeu d’éléments de collecte à démarrer, puis cliquez sur **Démarrer le jeu d’éléments de collecte de données**.  
  
     Une zone de message affiche les résultats de cette action et une flèche verte sur l'icône du jeu d'éléments de collecte indique que celui-ci a démarré.  
  
#### <a name="to-stop-a-collection-set"></a>Pour arrêter un jeu d'éléments de collecte  
  
1.  Dans l'Explorateur d'objets, développez le nœud **Gestion** et développez **Collecte de données**, puis **Jeux d'éléments de collecte de données système**.  
  
2.  Cliquez avec le bouton droit sur le jeu d’éléments de collecte à arrêter, puis cliquez sur **Arrêter le jeu d’éléments de collecte de données**.  
  
     Une zone de message affiche les résultats de cette action et un cercle rouge sur l'icône du jeu d'éléments de collecte indique que celui-ci s'est arrêté.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-start-a-collection-set"></a>Pour démarrer un jeu d'éléments de collecte  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_start_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-start-collection-set-transact-sql) pour démarrer le jeu d’éléments de collecte présentant l’ID `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_start_collection_set @collection_set_id = 1;  
```  
  
#### <a name="to-stop-a-collection-set"></a>Pour arrêter un jeu d'éléments de collecte  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_syscollector_stop_collection_set](/sql/relational-databases/system-stored-procedures/sp-syscollector-stop-collection-set-transact-sql) pour arrêter le jeu d’éléments de collecte présentant l’ID `1`.  
  
```sql  
USE msdb;  
GO  
EXEC sp_syscollector_stop_collection_set @collection_set_id = 1;  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Vues du collecteur de données &#40;Transact-SQL&#41;](/sql/relational-databases/system-catalog-views/data-collector-views-transact-sql)   
 [Collecte de données](data-collection.md)  
  
  
