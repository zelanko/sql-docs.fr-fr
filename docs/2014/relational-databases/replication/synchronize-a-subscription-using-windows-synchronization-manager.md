---
title: Synchroniser un abonnement à l’aide du gestionnaire de synchronisation Windows (gestionnaire de synchronisation Windows) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- synchronization [SQL Server replication], Windows Synchronization Manager
- Windows Synchronization Manager
ms.assetid: 80f15dd6-e84d-4f96-9866-5b34ea531f1e
author: MashaMSFT
ms.author: mathoma
ms.openlocfilehash: 49f1b0832fb82425874b656715091f793b79dfd5
ms.sourcegitcommit: 57f1d15c67113bbadd40861b886d6929aacd3467
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/18/2020
ms.locfileid: "85004485"
---
# <a name="synchronize-a-subscription-using-windows-synchronization-manager-windows-synchronization-manager"></a>synchroniser un abonnement à l'aide du Gestionnaire de synchronisation Windows (Windows Synchronization Manager)
  Le Gestionnaire de synchronisation[!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows ne peut être utilisé que pour synchroniser des abonnements à des publications Microsoft [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] est exécuté sur le même ordinateur que le Gestionnaire de synchronisation (il peut également servir à synchroniser des fichiers hors connexion et des pages Web). Pour utiliser le Gestionnaire de synchronisation :  
  
1.  Activez la synchronisation des abonnements par extraction à l’aide du gestionnaire de synchronisation Windows dans la boîte de dialogue Propriétés de l' **abonnement- \<Subscriber> : \<SubscriptionDatabase> ** . Pour plus d’informations sur l’accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un abonnement par extraction (pull)](view-and-modify-pull-subscription-properties.md).  
  
2.  Accédez au Gestionnaire de synchronisation par le menu **Démarrer** de Windows.  
  
 Le Gestionnaire de synchronisation vous permet d'utiliser l'outil de résolution interactive pour les abonnements de fusion. En général, les conflits détectés pendant la synchronisation sont résolus automatiquement, mais si la résolution interactive est activée, les conflits peuvent être résolus par un utilisateur pendant la synchronisation. Si une synchronisation est effectuée en dehors du Gestionnaire de synchronisation Windows (comme une synchronisation planifiée ou à la demande dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] ou le Moniteur de réplication), les conflits sont résolus automatiquement sans intervention de l'utilisateur, en fonction de l'outil de résolution spécifié pour l'article.  
  
> [!NOTE]  
>  À partir de [!INCLUDE[firstref_longhorn](../../includes/firstref-longhorn-md.md)] et [!INCLUDE[wiprlhlong](../../includes/wiprlhlong-md.md)], les versions 64 bits du Gestionnaire de synchronisation Windows ne peuvent pas détecter les abonnements 32 bits.  
  
### <a name="to-enable-the-synchronization-of-pull-subscriptions-with-windows-synchronization-manager"></a>Pour activer la synchronisation des abonnements par extraction de données (pull) avec le Gestionnaire de synchronisation Windows  
  
1.  Sur la page **général** de la boîte de dialogue Propriétés de l' **abonnement- \<Subscriber> \<SubscriptionDatabase> :** , sélectionnez la valeur **activer** pour l’option utiliser le **Gestionnaire de synchronisation Windows** .  
  
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-synchronize-a-pull-subscription-with-synchronization-manager"></a>Pour synchroniser un abonnement par extraction de données (pull) avec le Gestionnaire de synchronisation  
  
1.  Lancez le Gestionnaire de synchronisation au moyen de l'une des méthodes suivantes :  
  
    -   Dans Internet Explorer, cliquez sur **Outils**, puis sur **Synchroniser**.  
  
    -   Cliquez sur **Démarrer**, pointez sur **Programmes** ou **Tous les programmes**, puis sur **Accessoires**et cliquez sur **Synchroniser**.  
  
    -   Cliquez sur **Démarrer**, puis sur **exécuter.** Dans la boîte de dialogue **exécuter** , tapez `mobsync.exe` dans le champ **ouvrir** , puis cliquez sur **OK**.  
  
2.  Dans la boîte de dialogue **Éléments à synchroniser** , sélectionnez les abonnements à synchroniser. Les abonnements sont listés sous les instances [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] installées sur l'ordinateur.  
  
3.  Cliquez sur **Synchroniser**.  
  
### <a name="to-reinitialize-a-pull-subscription-with-synchronization-manager"></a>Pour réinitialiser un abonnement par extraction de données (pull) avec le Gestionnaire de synchronisation  
  
1.  Dans la boîte de dialogue **Éléments à synchroniser** , sélectionnez un abonnement, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de l'abonnement SQL Server** , cliquez sur **Réinitialiser l'abonnement**.  
  
3.  Cliquez sur **Oui**.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
     La prochaine fois qu'un abonnement est synchronisé, un nouvel instantané est appliqué par défaut sur la base de données d'abonnement. Pour plus d’informations, consultez [Réinitialiser des abonnements](reinitialize-subscriptions.md).  
  
> [!NOTE]  
>  La réplication de fusion permet aux modifications en suspens d'être chargées sur le serveur de publication avant que l'instantané ne soit appliqué, mais cette option n'est pas disponible dans le Gestionnaire de synchronisation. Pour charger les modifications, synchronisez l'abonnement avant de le réinitialiser.  
  
### <a name="to-set-properties-for-a-pull-subscription-in-synchronization-manager"></a>Pour définir les propriétés d'un abonnement par extraction de données (pull) dans le Gestionnaire de synchronisation  
  
1.  Dans la boîte de dialogue **Éléments à synchroniser** , sélectionnez un abonnement, puis cliquez sur **Propriétés**.  
  
2.  Affichez et modifiez les propriétés dans les onglets suivants :  
  
    -   **Identification**  
  
    -   **Connexion à l'Abonné**, **Connexion au serveur de distribution**et **Connexion au serveur de publication** (pour la réplication de fusion uniquement)  
  
    -   **Informations sur le serveur Web** (pour les abonnements de fusion sur les abonnés exécutant SQL Server 2005 ou supérieur)  
  
    -   **Autre**  
  
     Il est recommandé d'utiliser l'authentification Windows pour toutes les connexions. Pour plus d'informations sur les autorisations requises par l'Agent de distribution et l'Agent de fusion, consultez [Replication Agent Security Model](security/replication-agent-security-model.md).  
  
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-remove-a-pull-subscription-from-synchronization-manager"></a>Pour supprimer un abonnement par extraction de données (pull) à partir du Gestionnaire de synchronisation  
  
1.  Dans la boîte de dialogue **Éléments à synchroniser** , sélectionnez un abonnement, puis cliquez sur **Propriétés**.  
  
2.  Dans la boîte de dialogue **Propriétés de l'abonnement SQL Server** , cliquez sur **Supprimer l'abonnement**.  
  
3.  Sélectionnez une option dans la boîte de dialogue **Supprimer l'abonnement** .  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-use-the-interactive-resolver"></a>Pour utiliser l'outil de résolution interactive  
  
1.  Activez l'article et l'abonnement pour la résolution interactive. Pour plus d’informations, consultez [Spécifier la résolution interactive des conflits pour les articles de fusion](../../relational-databases/replication/publish/specify-merge-replication-properties.md#interactive-conflict-resolution).
  
2.  Une fois que l'abonnement commence la synchronisation dans le Gestionnaire de synchronisation, l'outil de résolution interactive est lancé automatiquement si la résolution interactive de conflits est activée et qu'il existe des conflits pour un ou plusieurs articles. L'outil de résolution interactive affiche les conflits un à la fois, avec une suggestion de résolution pour chaque conflit (basée sur l'outil de résolution spécifié lors de la création de la publication et de l'abonnement).  
  
3.  Modifiez au besoin toute colonne affichée dans l'outil de résolution interactive, puis cliquez sur l'un des boutons suivants pour résoudre le conflit :  
  
    -   **Accepter la suggestion**  
  
    -   **Accepter le serveur de publication**  
  
    -   **Accepter l'Abonné**  
  
    -   **Tout résoudre automatiquement** (tous les conflits actuels sont résolus sans données complémentaires)  
  
     La ligne sélectionné est ensuite appliqué au serveur de publication et/ou à l'Abonné ; elle est propagée à d'autres nœuds dans la topologie lors des synchronisations suivantes.  
  
> [!NOTE]  
>  Les modifications ne sont appliquées que si elles font partie de la ligne choisie pour la résolution. Par exemple, si vous effectuez des modifications sous le **Serveur de publication**, puis cliquez sur **Accepter l'Abonné**, les modifications sont ignorées.  
  
## <a name="see-also"></a>Voir aussi  
 [Résolution interactive des conflits](merge/advanced-merge-replication-conflict-interactive-resolution.md)  
  
