---
title: "Abonn&#233;s | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.rep.newsubwizard.subscribers.f1"
helpviewer_keywords: 
  - "Abonnés [SQL Server replication]"
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
caps.latest.revision: 26
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 26
---
# Abonn&#233;s
  Spécifiez le [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] les abonnés qui recevront un abonnement à la publication sélectionnée.  
  
## Options  
 **Abonnés**  
 Sélectionnez la case à cocher dans la grille pour activer correspondants [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] source de données en tant qu’abonné à la publication sélectionnée sur la **Publication** page. Si l'Abonné ne figure pas dans la liste, cliquez sur **Ajouter un abonné** ou **Ajouter un abonné SQL Server**.  
  
 **Base de données d'abonnement**  
 Les informations affichées dans et les actions disponibles à partir de cette colonne dépendent du type d’abonné répertorié dans le **abonnés** colonne :  
  
-   Pour les abonnés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez une base de données d'abonnement dans la liste **Base de données d'abonnement** ou créez une base de données en sélectionnant la commande **Nouvelle base de données** dans la même liste.  
  
    > [!NOTE]  
    >  Si vous activez le serveur de publication en tant qu'abonné, la base de données d'abonnement doit être différente de la base de données de publication.  
  
-   Pour les abonnés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], la base de données d'abonnement n'est pas affichée. Spécifiez la base de données, ainsi que d’autres informations de connexion, dans le **nom de source de données** champ le **Ajouter non-SQL Server** boîte de dialogue. Cette boîte de dialogue est disponible en cliquant sur **Ajouter un abonné** puis en cliquant sur **Ajouter un abonné non-SQL Server**.  
  
 **Ajouter un abonné**  
 Ajoute un serveur à la liste des serveurs pouvant être activés comme abonnés. Ce bouton s'affiche lorsque toutes les conditions suivantes sont vraies :  
  
-   La publication que vous avez sélectionnée est un instantané ou une publication transactionnelle qui ne prend pas en charge la mise à jour des abonnements.  
  
    > [!NOTE]  
    >  Si la publication à laquelle vous vous abonnez a des abonnements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et qu'elle n'est pas déjà activée pour les abonnements non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], vous ne pouvez pas ajouter d'abonnement non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)].  
  
-   L'abonnement est un abonnement par envoi de données (push).  
  
-   Le serveur de la publication sélectionnée est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou une version ultérieure.  
  
 En cliquant sur **Ajouter un abonné** affiche un menu contenant deux options : **Ajouter un abonné SQL Server** et **Ajouter un abonné non-SQL Server**. Cliquez sur **Ajouter un abonné non-SQL Server** pour ajouter une Oracle ou un abonné IBM DB2.  
  
 **Ajouter un Abonné SQL Server**  
 Ajoute un serveur à la liste des serveurs pouvant être activés comme abonnés. Ce bouton s'affiche lorsqu'au moins une des conditions suivantes est vraie :  
  
-   La publication que vous avez sélectionnée est une publication de fusion, un instantané ou une publication transactionnelle qui prend en charge la mise à jour des abonnements.  
  
-   L'abonnement est un abonnement par extraction de données (pull).  
  
-   Le serveur de la publication sélectionnée est antérieure à la version [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour les versions antérieures, le bouton s'affiche uniquement si l'une des conditions suivantes est vraie :  
  
    -   Vous êtes membre du rôle serveur fixe **sysadmin** sur le serveur de publication.  
  
    -   L'Abonné a été ajouté à la page **Abonnés** de la boîte de dialogue **Propriétés du serveur de publication** .  
  
    -   La publication autorise les abonnements anonymes.  
  
## Voir aussi  
 [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  