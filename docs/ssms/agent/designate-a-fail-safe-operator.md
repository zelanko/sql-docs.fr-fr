---
title: "Désigner un opérateur de prévention de défaillance | Microsoft Docs"
ms.custom: 
ms.date: 01/19/2017
ms.prod: sql-non-specified
ms.reviewer: 
ms.suite: 
ms.technology: tools-ssms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- SQL Server Agent jobs, operators
- fail-safe operator [SQL Server]
- jobs [SQL Server Agent], operators
- notifications [SQL Server], job status
ms.assetid: 0f4eb513-5c0a-4523-974e-e85c1deeb57f
caps.latest.revision: "4"
author: stevestein
ms.author: sstein
manager: jhubbard
ms.workload: Inactive
ms.openlocfilehash: ece54455e161fb80bed3cd2476eae0ca7f585678
ms.sourcegitcommit: 9678eba3c2d3100cef408c69bcfe76df49803d63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/09/2017
---
# <a name="designate-a-fail-safe-operator"></a>Désigner un opérateur de prévention de défaillance
Un opérateur de prévention de défaillance est un utilisateur qui reçoit l'alerte si l'opérateur désigné n'est pas joignable. Cette rubrique explique comment définir un opérateur de prévention de défaillance qui recevra les notifications d’alertes de [!INCLUDE[msCoName](../../includes/msconame_md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans [!INCLUDE[ssCurrent](../../includes/sscurrent_md.md)] à l’aide de [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)].  
  
**Dans cette rubrique**  
  
-   **Avant de commencer :**  
  
    [Limitations et restrictions](#Restrictions)  
  
    [Sécurité](#Security)  
  
-   **Pour désigner un opérateur de prévention de défaillance, utilisez :**  
  
    [SQL Server Management Studio](#SSMSProcedure)  
  
## <a name="BeforeYouBegin"></a>Avant de commencer  
  
### <a name="Restrictions"></a>Limitations et restrictions  
  
-   Les options du récepteur de radiomessagerie et **net send** seront supprimées de [!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)] Agent dans une version future de [!INCLUDE[msCoName](../../includes/msconame_md.md)][!INCLUDE[ssNoVersion](../../includes/ssnoversion_md.md)]. Évitez d'utiliser ces fonctionnalités dans une nouvelle tâche de développement et prévoyez de modifier les applications qui les utilisent actuellement.  
  
-   Remarque : SQL Server Agent doit être configuré pour utiliser la messagerie de base de données pour envoyer des notifications aux opérateurs par messagerie électronique ou radiomessagerie. Pour plus d'informations, consultez [Affecter des alertes à un opérateur](http://msdn.microsoft.com/library/ms190038.aspx).  
  
-   [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull_md.md)] est un outil dont l'interface graphique permet de gérer facilement les travaux. Son utilisation est recommandée pour créer et gérer l'infrastructure des travaux.  
  
### <a name="Security"></a>Sécurité  
  
#### <a name="Permissions"></a>Permissions  
Seuls les membres du rôle serveur fixe **sysadmin** peuvent désigner des opérateurs de prévention de défaillance.  
  
## <a name="SSMSProcedure"></a>Utilisation de SQL Server Management Studio  
  
#### <a name="to-designate-a-fail-safe-operator"></a>Pour désigner un opérateur de prévention de défaillance  
  
1.  Dans **l’Explorateur d’objets** , cliquez sur le signe plus pour développer le serveur qui contient l’opérateur de SQL Server Agent que vous souhaitez désigner comme opérateur de prévention de défaillance.  
  
2.  Cliquez avec le bouton droit sur **SQL Server Agent** , puis sélectionnez **Propriétés**.  
  
3.  Dans la boîte de dialogue **Propriétés de l’Agent SQL Server –***nom_serveur* , sous **Sélectionner une page**, sélectionnez **Système d’alerte**.  
  
4.  Sous **Opérateur de prévention de défaillance**, sélectionnez **Activer l’opérateur de prévention de défaillance**.  
  
5.  Dans la liste **Opérateur** , sélectionnez l’opérateur que vous souhaitez définir comme opérateur de prévention de défaillance.  
  
6.  Cochez tout ou partie des cases suivantes pour spécifier comment l’opérateur doit être informé : **Messagerie électronique**, **Radiomessagerie**ou **NET SEND**.  
  
7.  Lorsque vous avez terminé, cliquez sur **OK**.  
  
