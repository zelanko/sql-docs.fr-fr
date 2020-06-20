---
title: Créer un serveur maître | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: ssms
ms.topic: conceptual
f1_keywords:
- sql12.ag.msxwiz.complete.f1
- sql12.ag.msxwiz.target.f1
- sql12.ag.msxwiz.login.f1
- sql12.ag.msxwiz.cover.f1
- sql12.ag.msxwiz.operator.f1
helpviewer_keywords:
- master servers [SQL Server], creating
- wizards [SQL Server Management Studio], Master Server Wizard
- SQL Server Agent jobs, master servers
- Master Server Wizard
ms.assetid: 05739a73-1fdf-4d9d-92a6-70f328380322
author: stevestein
ms.author: sstein
ms.openlocfilehash: ce8e7428aaf8ba459bcf6831988c61da3f192bac
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85008761"
---
# <a name="make-a-master-server"></a>Créer un serveur maître
  Cette rubrique décrit comment définir un serveur maître [!INCLUDE[ssCurrent](../../includes/sscurrent-md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou [!INCLUDE[tsql](../../includes/tsql-md.md)].  
  
 **Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
     [Sécurité](#Security)  
  
-   **Pour créer un serveur maître à l'aide de :**  
  
     [SQL Server Management Studio](#SSMSProcedure)  
  
     [Transact-SQL](#TsqlProcedure)  
  
##  <a name="before-you-begin"></a><a name="BeforeYouBegin"></a> Avant de commencer  
  
###  <a name="security"></a><a name="Security"></a> Sécurité  
 Les travaux distribués dont les étapes sont associées à un proxy sont exécutés dans le contexte du compte proxy du serveur cible. Assurez-vous que les conditions suivantes sont remplies ou que les étapes de travail associées à un proxy ne seront pas téléchargées du serveur maître vers la cible :  
  
-   La sous-clé de Registre du serveur maître **\ HKEY_LOCAL_MACHINE \SOFTWARE\Microsoft\Microsoft SQL Server \\ < *instance_name*> \SQL Server Agent\AllowDownloadedJobsToMatchProxyName** (REG_DWORD) a la valeur 1 (true). Par défaut, la valeur de cette sous-clé est 0 (False).  
  
-   Il existe sur le serveur cible un compte proxy possédant le même nom que le compte proxy du serveur maître sur lequel l'étape du travail est exécutée.  
  
 Si les étapes du travail utilisant des comptes proxy échouent pendant leur téléchargement à partir du serveur maître vers le serveur cible, vous pouvez vérifier la colonne **error_message** dans la table **sysdownloadlist** de la base de données **msdb** pour les messages d’erreur suivants :  
  
-   « L'étape du travail nécessite un compte proxy, cependant la mise en correspondance de proxy est désactivée sur le serveur cible. »  
  
     Pour corriger ce problème, affectez à la sous-clé de Registre **AllowDownloadedJobsToMatchProxyName** la valeur 1.  
  
-   « Proxy introuvable. »  
  
     Pour résoudre ce problème, vérifiez qu'un compte proxy portant le même nom que le compte proxy du serveur maître sous lequel l'étape s'exécute existe sur le serveur cible.  
  
####  <a name="permissions"></a><a name="Permissions"></a> Autorisations  
 Les autorisations d'exécution de cette procédure sont octroyées par défaut aux membres du rôle serveur fixe `sysadmin`.  
  
##  <a name="using-sql-server-management-studio"></a><a name="SSMSProcedure"></a> Utilisation de SQL Server Management Studio  
  
#### <a name="to-make-a-master-server"></a>Pour créer un serveur maître  
  
1.  Dans **l’Explorateur d'objets**, connectez-vous à une instance [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] et développez-la.  
  
2.  Cliquez avec le bouton droit sur **Agent SQL Server**, pointez sur **Administration multiserveur**, puis cliquez sur **Transformer en serveur maître**. L' **Assistant Serveur maître** vous guide au sein du processus de définition d'un serveur maître et d'ajout de serveurs cibles.  
  
3.  Dans la page **Opérateur de serveur maître** , configurez un opérateur pour le serveur maître. Pour envoyer des notifications par e-mail ou par récepteur de radiomessagerie aux opérateurs, [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent doit être configuré pour l’envoi d’e-mail. Pour envoyer des notifications aux opérateurs au moyen de **net send**, le service Messenger doit s’exécuter sur le serveur où réside [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] Agent.  
  
     **Adresse de messagerie**  
     Permet de spécifier l'adresse de messagerie de l'opérateur.  
  
     **Adresse de radiomessagerie**  
     Permet de spécifier l'adresse de radiomessagerie de l'opérateur.  
  
     **Adresse d'envoi réseau**  
     Permet de spécifier l’adresse **net send** de l’opérateur.  
  
4.  Dans la page **Serveur cible** , sélectionnez les serveurs cibles pour le serveur maître.  
  
     **Serveurs inscrits**  
     Répertorie les serveurs inscrits dans Microsoft [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] qui ne sont pas déjà des serveurs cibles.  
  
     **Serveurs cibles**  
     Répertorie les serveurs qui sont des serveurs cibles.  
  
     **>**  
     Déplace le serveur sélectionné vers la liste des serveurs cibles.  
  
     **>>**  
     Déplace tous les serveurs vers la liste des serveurs cibles.  
  
     **<**  
     Supprime le serveur sélectionné de la liste des serveurs cibles.  
  
     **<<**  
     Supprime tous les serveurs de la liste des serveurs cibles.  
  
     **Ajouter une connexion**  
     Ajoute un serveur à la liste des serveurs cibles sans inscrire le serveur.  
  
     **Connection**  
     Modifie les propriétés de connexion du serveur sélectionné.  
  
5.  Dans la page **Infos d'identification de connexion du serveur maître** , spécifiez si vous souhaitez créer une connexion pour le serveur cible, le cas échéant, et lui attribuer des droits sur le serveur maître.  
  
     **Créer une nouvelle connexion si nécessaire et lui attribuer des droits sur le serveur MSX**  
     Créez une nouvelle connexion sur le serveur cible si la connexion spécifiée n'existe pas encore.  
  
##  <a name="using-transact-sql"></a><a name="TsqlProcedure"></a> Utilisation de Transact-SQL  
  
#### <a name="to-make-a-master-server"></a>Pour créer un serveur maître  
  
1.  Connectez-vous au [!INCLUDE[ssDE](../../includes/ssde-md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**. Cet exemple inscrit le serveur actuel dans le serveur maître AdventureWorks1. L'emplacement du serveur actuel est Building 21, Room 309, Rack 5.  
  
```  
USE msdb ;  
GO  
  
EXEC dbo.sp_msx_enlist N'AdventureWorks1',   
    N'Building 21, Room 309, Rack 5' ;   
GO;  
```  
  
 Pour plus d’informations, consultez [sp_msx_enlist &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-msx-enlist-transact-sql).  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un environnement multiserveur](create-a-multiserver-environment.md)   
 [Administration automatisée à l'échelle d'une entreprise](automated-administration-across-an-enterprise.md)  
  
  
