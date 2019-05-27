---
title: Définir le compte du service du Lanceur de démon de filtre de texte intégral | Microsoft Docs
ms.custom: ''
ms.date: 04/27/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: search
ms.topic: conceptual
helpviewer_keywords:
- full-text search [SQL Server], FDHOST Launcher (MSSQLFDLauncher) service account
- FDHOST Launcher (MSSQLFDLauncher) [SQL Server]
ms.assetid: 3ab1d101-7ae0-488f-9b57-468e2517b737
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: 8f327cefbb916bf83f695db40a1d3c3025b7a5d2
ms.sourcegitcommit: 45a9d7ffc99502c73f08cb937cbe9e89d9412397
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2019
ms.locfileid: "66010935"
---
# <a name="set-the-service-account-for-the-full-text-filter-daemon-launcher"></a>Définir le compte du service du Lanceur de démon de filtre de texte intégral
  Cette rubrique explique comment définir le compte du service du Lanceur de démon de filtre de texte intégral SQL (MSSQLFDLauncher) à l'aide du Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le service du Lanceur de démon de filtre de texte intégral SQL est utilisé par la recherche en texte intégral ssNoVersion pour démarrer le processus hôte de démon de filtre, qui gère les césures de mots et le filtrage de recherche en texte intégral. Ce service doit être en cours d'exécution pour que la recherche en texte intégral puisse être utilisée.  
  
 Le service du Lanceur de démon de filtre de texte intégral SQL est un service dépendant associé à une instance spécifique de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. Le service du Lanceur de démon de filtre de texte intégral SQL propage les informations du compte de service à chaque processus hôte de démon de filtre.  
  
  
##  <a name="setting"></a> Définition du compte de Service  
  
#### <a name="to-set-the-sql-full-text-filter-daemon-launcher-service-account-for-full-text-search"></a>Pour définir le compte du service du Lanceur de démon de filtre de texte intégral SQL pour la recherche en texte intégral  
  
1.  Dans le menu **Démarrer** , pointez sur **Tous les programmes**, sur [!INCLUDE[ssCurrentUI](../../includes/sscurrentui-md.md)]et sur **Outils de configuration**, puis cliquez sur **Gestionnaire de configuration SQL Server**.  
  
2.  Dans **Gestionnaire de Configuration SQL Server**, cliquez sur **SQL Server Services**, avec le bouton droit **Lanceur de démon de filtre de recherche en texte intégral SQL (*`instance name`*)** , puis cliquez sur **propriétés**.  
  
3.  Cliquez sur l’onglet **Ouvrir une session** de la boîte de dialogue, puis sélectionnez ou entrez le nom du compte sous lequel chaque processus créé par le service du Lanceur de démon de filtre de texte intégral SQL doit s’exécuter.  
  
4.  Après avoir fermé la boîte de dialogue, cliquez sur **Redémarrer** pour redémarrer le service du Lanceur de démon de filtre de texte intégral SQL.  
  
  
##  <a name="error"></a> Si le filtre de texte intégral SQL Service Lanceur de démon ne démarre pas  
 L'échec du démarrage du service du Lanceur de démon de filtre de texte intégral SQL peut être dû à l'une ou plusieurs des causes suivantes :  
  
-   Le mot de passe associé au compte du service du Lanceur de démon de filtre de texte intégral SQL a expiré.  
  
     Si vous utilisez un compte d'utilisateur local pour le service du Lanceur de démon de filtre de texte intégral SQL et que votre mot de passe expire, vous devez effectuer les actions suivantes :  
  
    1.  Définissez un nouveau mot de passe Windows pour le compte.  
  
    2.  Dans le Gestionnaire de configuration [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], mettez à jour le service du Lanceur de démon de filtre de texte intégral SQL de sorte qu'il utilise le nouveau mot de passe.  
  
-   Le compte ou le mot de passe d'utilisateur du compte de service est incorrect.  
  
     Il se peut que le service du Lanceur de démon de filtre de texte intégral SQL tente de se connecter avec un compte et un mot de passe d'utilisateur incorrects. Suivez les procédures précédentes pour vérifier que le compte d'utilisateur du service n'a pas été modifié.  
  
-   Le compte utilisé pour se connecter au service ne dispose pas de privilèges.  
  
     Il se peut que vous utilisiez un compte qui ne dispose pas de privilèges de connexion sur l'ordinateur où est installée l'instance de serveur. Vérifiez que vous vous connectez avec un compte qui dispose de droits et d'autorisations d'utilisateur sur l'ordinateur local.  
  
-   Une autre instance du même canal nommé est déjà en cours d'exécution.  
  
     Le service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] fait office de serveur de canaux nommés pour le client du service du Lanceur de démon de filtre de texte intégral SQL. Si le canal nommé a déjà été créé par un autre processus préalablement au démarrage de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] , une erreur est consignée dans le journal des erreurs de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] et dans le journal des événements Windows, et la recherche en texte intégral n'est pas disponible.  Identifiez le processus ou l'application qui tente d'utiliser le même canal nommé et arrêtez l'application.  
  
-   Le service du Lanceur de démon de filtre de texte intégral SQL n'est pas configuré correctement.  
  
     Il se peut que le service ne soit pas correctement configuré sur l'ordinateur local.  
  
     Si la fonctionnalité des canaux nommés a été désactivée sur l'ordinateur local ou si [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] a été configuré pour utiliser un autre canal nommé que celui défini par défaut, le service du Lanceur de démon de filtre de texte intégral SQL peut ne pas démarrer.  
  
-   Le groupe de services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] n'est pas autorisé à démarrer le service du Lanceur de démon de filtre de texte intégral SQL.  
  
     Pendant l'installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le groupe de services [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] se voit accorder une autorisation par défaut de gérer, d'interroger et de démarrer le service du Lanceur de démon de filtre de texte intégral SQL. Si les autorisations de groupe de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] affectées au compte de service du Lanceur de démon de filtre de texte intégral SQL ont été supprimées après l’installation de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)], le service du Lanceur de démon de filtre de texte intégral SQL ne démarre pas et la recherche en texte intégral est désactivée. Vérifiez que le groupe de service [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] dispose d’autorisations concernant le compte du service du Lanceur de démon de filtre de texte intégral SQL.  
  
  
## <a name="see-also"></a>Voir aussi  
 [Rubriques de procédures concernant la gestion des services &#40;Gestionnaire de configuration SQL Server&#41;](../../database-engine/managing-services-how-to-topics-sql-server-configuration-manager.md)  
 [Mise à niveau de la fonction de recherche en texte intégral](upgrade-full-text-search.md)  
  
  
