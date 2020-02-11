---
title: Abonnés | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql12.rep.newsubwizard.subscribers.f1
helpviewer_keywords:
- Subscribers [SQL Server replication]
ms.assetid: 43fb2454-c220-4d25-a826-83c332eb00d2
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 725be263e30687a3f2ded90990e952e1cd97a185
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "62629386"
---
# <a name="subscribers"></a>Abonnés
  Spécifiez [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] le ou les[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] abonnés non-qui vont recevoir un abonnement à la publication sélectionnée.  
  
## <a name="options"></a>Options  
 **Abonnés**  
 Activez la case à cocher dans la grille pour activer [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] la source correspondante[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ou non, en tant qu’abonné, à la publication choisie sur la page **publication** . Si l'Abonné ne figure pas dans la liste, cliquez sur **Ajouter un abonné** ou **Ajouter un abonné SQL Server**.  
  
 **Base de données d’abonnement**  
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
  
-   L’éditeur de la publication sélectionnée est [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] ou version ultérieure.  
  
 Cliquez sur **Ajouter un abonné** pour afficher un menu contenant deux options : **Ajouter un Abonné SQL Server** et **Ajouter un Abonné non-SQL Server**. Cliquez sur **Ajouter un Abonné non-SQL Server** pour ajouter un abonné Oracle ou IBM DB2.  
  
 **Ajouter SQL Server abonné**  
 Ajoute un serveur à la liste des serveurs pouvant être activés comme abonnés. Ce bouton s'affiche lorsqu'au moins une des conditions suivantes est vraie :  
  
-   La publication que vous avez sélectionnée est une publication de fusion, un instantané ou une publication transactionnelle qui prend en charge la mise à jour des abonnements.  
  
-   L'abonnement est un abonnement par extraction de données (pull).  
  
-   Le serveur de la publication sélectionnée est antérieure à la version [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)]. Pour les versions antérieures, le bouton s'affiche uniquement si l'une des conditions suivantes est vraie :  
  
    -   Vous êtes membre du rôle serveur fixe **sysadmin** sur le serveur de publication.  
  
    -   L'Abonné a été ajouté à la page **Abonnés** de la boîte de dialogue **Propriétés du serveur de publication** .  
  
    -   La publication autorise les abonnements anonymes.  
  
## <a name="see-also"></a>Voir aussi  
 [Create a Pull Subscription](create-a-pull-subscription.md)   
 [Create a Push Subscription](create-a-push-subscription.md)   
 [Non-SQL Server Subscribers](non-sql/non-sql-server-subscribers.md)   
 [S'abonner à des publications](subscribe-to-publications.md)  
  
  
