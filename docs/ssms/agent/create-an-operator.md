---
title: "Créer un opérateur | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology:
- tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- jobs [SQL Server Agent], notification options
- operators (users) [Database Engine], creating with Management Studio
- SQL Server Agent jobs, notification options
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 1359d790-5905-4927-a208-e7155e7768a2
caps.latest.revision: 5
author: stevestein
ms.author: sstein
manager: jhubbard
ms.translationtype: Human Translation
ms.sourcegitcommit: 2edcce51c6822a89151c3c3c76fbaacb5edd54f4
ms.openlocfilehash: afca596bc8dc55411bcfbd48b74d3bdfd7c11248
ms.contentlocale: fr-fr
ms.lasthandoff: 04/11/2017

---
# <a name="create-an-operator"></a>Créer un opérateur
Cette rubrique explique comment configurer un compte d’utilisateur pour qu'il reçoive des notifications relatives aux travaux de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l'aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] ou de [!INCLUDE[tsql](../../includes/tsql_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour créer un opérateur, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
    [Transact-SQL](#TsqlProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   Les options du récepteur de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans une version future de [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   Remarque : SQL Server Agent doit être configuré pour utiliser la messagerie de base de données pour envoyer des notifications aux opérateurs par messagerie électronique ou radiomessagerie. Pour plus d'informations, consultez [Affecter des alertes à un opérateur](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Seuls les membres du rôle serveur fixe **sysadmin** peuvent créer des opérateurs.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-create-an-operator"></a>Pour créer un opérateur  
  
1.  Dans l' **Explorateur d'objets**, cliquez sur le signe plus (+) pour développer le serveur sur lequel vous souhaitez créer un opérateur de SQL Server Agent.  
  
2.  Cliquez sur le signe plus (+) pour développer **Agent SQL Server**.  
  
3.  Cliquez avec le bouton droit sur le dossier **Opérateurs** , puis sélectionnez **Nouvel opérateur**.  
  
    Les options suivantes sont disponibles sur la page **Général** de la boîte de dialogue **Nouvel opérateur** :  
  
    **Nom**  
    Permet de modifier le nom de l'opérateur.  
  
    **Activé**  
    Permet d'activer l'opérateur. Aucune notification n'est envoyée à l'opérateur lorsque cette option est désactivée.  
  
    **Nom de messagerie électronique**  
    Spécifie l'adresse de messagerie de l'opérateur.  
  
    **Adresse d'envoi réseau**  
    Spécifie l’adresse à utiliser pour **net send**.  
  
    **Nom de l'adresse de radiomessagerie**  
    Spécifie l'adresse de messagerie à utiliser pour la radiomessagerie de l'opérateur.  
  
    **Planification de la radiomessagerie active**  
    Définit les périodes d'activité de la radiomessagerie.  
  
    **Lundi - Dimanche**  
    Permet de sélectionner les jours d'activité de la radiomessagerie.  
  
    **Début de journée**  
    Sélectionne l’heure après laquelle l’Agent [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] envoie des messages à la radiomessagerie.  
  
    **Fin de journée**  
    Sélectionne l’heure après laquelle [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent n’envoie plus de messages à la radiomessagerie.  
  
    Les options suivantes sont disponibles sur la page **Notifications** de la boîte de dialogue **Nouvel opérateur** :  
  
    **Alertes**  
    Affiche les alertes dans l'instance.  
  
    **Travaux**  
    Affiche les travaux dans l'instance.  
  
    **Liste d'alertes**  
    Affiche la liste des alertes dans l'instance.  
  
    **Liste des travaux**  
    Affiche la liste des travaux dans l'instance.  
  
    **Courrier électronique**  
    Notifie cet opérateur à l'aide d'un courrier électronique.  
  
    **Récepteur de radiomessagerie**  
    Notifie cet opérateur en envoyant un courrier électronique à son adresse de radiomessagerie.  
  
    **Envoi réseau**  
    Notifie cet opérateur à l’aide de **net send**.  
  
4.  Lorsque la création du nouvel opérateur est terminée, cliquez sur **OK**.  
  
## <a name="TsqlProcedure"></a>Utilisation de Transact-SQL  
  
#### <a name="to-create-an-operator"></a>Pour créer un opérateur  
  
1.  Dans l' **Explorateur d'objets**, connectez-vous à une instance de [!INCLUDE[ssDE](../../includes/ssde_md.md)].  
  
2.  Dans la barre d'outils standard, cliquez sur **Nouvelle requête**.  
  
3.  Copiez et collez l'exemple suivant dans la fenêtre de requête, puis cliquez sur **Exécuter**.  
  
    ```  
    -- sets up the operator information for user 'danwi.'
    -- The operator is enabled.   
    -- SQL Server Agent sends notifications by pager 
    -- from Monday through Friday from 8 A.M. to 5 P.M.  
    USE msdb ;  
    GO  
  
    EXEC dbo.sp_add_operator  
        @name = N'Dan Wilson',  
        @enabled = 1,  
        @email_address = N'danwi',  
        @pager_address = N'5551290AW@pager.Adventure-Works.com',  
        @weekday_pager_start_time = 080000,  
        @weekday_pager_end_time = 170000,  
        @pager_days = 62 ;  
    GO  
    ```  
  
Pour plus d’informations, consultez [sp_add_operator (Transact-SQL)](http://msdn.microsoft.com/en-us/817cd98a-4dff-4ed8-a546-f336c144d1e0).  
  

