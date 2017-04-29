---
title: "Abonnés | Microsoft Docs"
ms.custom: 
ms.date: 03/14/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- replication
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
caps.latest.revision: 26
author: BYHAM
ms.author: rickbyh
manager: jhubbard
translationtype: Human Translation
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 1a7a3174c0eab10b0a05dd4844e214f3ab70ee75
ms.lasthandoff: 04/11/2017

---
# <a name="subscribers"></a>Abonnés
  Définissez les abonnés [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] qui doivent recevoir un abonnement à la publication sélectionnée.  
  
## <a name="options"></a>Options  
 **Abonnés**  
 Activez la case à cocher dans la grille pour activer la source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] correspondante sous la forme d'un abonné à la publication sélectionnée dans la page **Publication** . Si l'Abonné ne figure pas dans la liste, cliquez sur **Ajouter un abonné** ou **Ajouter un abonné SQL Server**.  
  
 **Base de données d'abonnement**  
 Les informations affichées et les actions disponibles dépendent du type d'abonné sélectionné dans la colonne **Abonnés** :  
  
-   Pour les abonnés [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , sélectionnez une base de données d'abonnement dans la liste **Base de données d'abonnement** ou créez une base de données en sélectionnant la commande **Nouvelle base de données** dans la même liste.  
  
    > [!NOTE]  
    >  Si vous activez le serveur de publication en tant qu'abonné, la base de données d'abonnement doit être différente de la base de données de publication.  
  
-   Pour les abonnés[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , la base de données d'abonnement n'est pas affichée. Définissez la base de données, ainsi que les autres informations de connexion, dans le champ **Nom de la source de données** de la boîte de dialogue **Ajouter un Abonné non-SQL Server** . Cette boîte de dialogue est disponible en cliquant sur **Ajouter un abonné** et sur **Ajouter un Abonné non-SQL Server**.  
  
 **Ajouter un abonné**  
 Ajoute un serveur à la liste des serveurs pouvant être activés comme abonnés. Ce bouton s'affiche lorsque toutes les conditions suivantes sont vraies :  
  
-   La publication que vous avez sélectionnée est un instantané ou une publication transactionnelle qui ne prend pas en charge la mise à jour des abonnements.  
  
    > [!NOTE]  
    >  Si la publication à laquelle vous vous abonnez a des abonnements [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et qu'elle n'est pas déjà activée pour les abonnements non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , vous ne pouvez pas ajouter d'abonnement non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .  
  
-   L'abonnement est un abonnement par envoi de données (push).  
  
-   Le serveur de la publication sélectionnée est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou une version ultérieure.  
  
 Cliquez sur **Ajouter un abonné** pour afficher un menu contenant deux options : **Ajouter un Abonné SQL Server** et **Ajouter un Abonné non-SQL Server**. Cliquez sur **Ajouter un Abonné non-SQL Server** pour ajouter un abonné Oracle ou IBM DB2.  
  
 **Ajouter un abonné SQL Server**  
 Ajoute un serveur à la liste des serveurs pouvant être activés comme abonnés. Ce bouton s'affiche lorsqu'au moins une des conditions suivantes est vraie :  
  
-   La publication que vous avez sélectionnée est une publication de fusion, un instantané ou une publication transactionnelle qui prend en charge la mise à jour des abonnements.  
  
-   L'abonnement est un abonnement par extraction de données (pull).  
  
-   Le serveur de la publication sélectionnée est antérieure à la version [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour les versions antérieures, le bouton s'affiche uniquement si l'une des conditions suivantes est vraie :  
  
    -   Vous êtes membre du rôle serveur fixe **sysadmin** sur le serveur de publication.  
  
    -   L'Abonné a été ajouté à la page **Abonnés** de la boîte de dialogue **Propriétés du serveur de publication** .  
  
    -   La publication autorise les abonnements anonymes.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer un abonnement par extraction](../../relational-databases/replication/create-a-pull-subscription.md)   
 [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md)   
 [Abonnés non-SQL Server](../../relational-databases/replication/non-sql/non-sql-server-subscribers.md)   
 [S’abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  
