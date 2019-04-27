---
title: Afficher ou configurer des options de connexion au serveur distant (SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: configuration
ms.topic: conceptual
helpviewer_keywords:
- remote servers [SQL Server], connection options
- servers [SQL Server], remote
- connections [SQL Server], remote servers
ms.assetid: 356d3e6b-8514-4bd2-a683-9de147949b2b
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 5dfc0aa145f106fc57c25a6249b928ee27ab4b87
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62757204"
---
# <a name="view-or-configure-remote-server-connection-options-sql-server"></a>Afficher ou configurer des options de connexion au serveur distant (SQL Server)
  Cette rubrique explique comment afficher ou configurer des options de connexion au serveur distant au niveau du serveur dans [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou de [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour afficher ou configurer des options de connexion au serveur distant, utilisez :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
-   **Suivi :**  [Après avoir configuré des options de connexion au serveur distant](#FollowUp)  
  
##  <a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="Security"></a> Sécurité  
  
####  <a name="Permissions"></a> Autorisations  
 L’exécution de **sp_serveroption** nécessite l’autorisation ALTER ANY LINKED SERVER sur le serveur.  
  
##  <a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-view-or-configure-remote-server-connection-options"></a>Pour afficher ou configurer des options de connexion au serveur distant  
  
1.  Dans l’Explorateur d’objets, cliquez avec le bouton droit sur un serveur, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de SQL Server - \<***nom_serveur***>**, cliquez sur **Connexions**.  
  
3.  Sur la page **Connexions** , vérifiez les paramètres **Connexions au serveur distant** et au besoin modifiez-les.  
  
4.  Répétez les étapes 1 à 3 sur l'autre serveur de la paire de serveurs distants.  
  
##  <a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-view-remote-server-connection-options"></a>Pour afficher les options de connexion au serveur distant  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple utilise [sp_helpserver](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql) pour retourner des informations sur tous les serveurs distants.  
  
```sql  
USE master;  
GO  
EXEC sp_helpserver ;  
```  
  
#### <a name="to-configure-remote-server-connection-options"></a>Pour configurer des options de connexion au serveur distant  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple montre comment utiliser [sp_serveroption](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql) pour configurer un serveur distant. Cet exemple configure un serveur distant correspondant à une autre instance de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], `SEATTLE3`, de façon à ce qu'il soit compatible avec le classement de l'instance locale de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
```sql  
USE master;  
EXEC sp_serveroption 'SEATTLE3', 'collation compatible', 'true';  
```  
  
##  <a name="FollowUp"></a> Suivi : Après avoir configuré des options de connexion au serveur distant  
 Le serveur distant doit être arrêté et redémarré pour que le paramètre puisse prendre effet.  
  
## <a name="see-also"></a>Voir aussi  
 [Options de configuration de serveur &#40;SQL Server&#41;](server-configuration-options-sql-server.md)   
 [Serveurs distants](remote-servers.md)   
 [Serveurs liés &#40;moteur de base de données&#41;](../../relational-databases/linked-servers/linked-servers-database-engine.md)   
 [sp_linkedservers &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-linkedservers-transact-sql)   
 [sp_helpserver &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-helpserver-transact-sql)   
 [sp_serveroption &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-serveroption-transact-sql)  
  
  
