---
title: "configurer des alertes de r&#233;plication pr&#233;d&#233;finies (SQL Server Management Studio) | Microsoft Docs"
ms.custom: ""
ms.date: "03/14/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "replication"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "alertes [SQL Server replication]"
  - "alertes de réplication prédéfinies [réplication SQL Server]"
ms.assetid: c0414147-7ffe-4f9a-908c-71c1b5201584
caps.latest.revision: 24
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 24
---
# configurer des alertes de r&#233;plication pr&#233;d&#233;finies (SQL Server Management Studio)
  La réplication comporte les alertes prédéfinies suivantes, qui peuvent être configurées pour répondre aux événements de réplication :  
  
-   **Réplication : succès de l'agent**  
  
-   **Réplication : échec de l'agent**  
  
-   **Réplication : nouvelle tentative de l'agent**  
  
-   **Réplication : suppression de l'abonnement expiré**  
  
-   **Réplication : abonnement réinitialisé après l'échec de validation**  
  
-   **Réplication : l'Abonné n'a pas réussi la validation des données**  
  
-   **Réplication : l'Abonné a passé la validation des données**  
  
-   **Réplication : arrêt personnalisé de l'Agent**  
  
 Configurer ces alertes à partir de la **alertes** dossier [!INCLUDE[msCoName](../../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../../includes/ssmanstudiofull-md.md)] ou **avertissements** onglet du moniteur de réplication. Pour plus d’informations sur l’accès à cet onglet, consultez [afficher des informations et effectuer des tâches pour un abonnement & #40 ; Moniteur de réplication & #41 ;](../../../relational-databases/replication/monitor/view-information-and-perform-tasks-for-a-subscription-replication-monitor.md).  
  
 En plus de ces alertes, le moniteur de réplication comprend un ensemble d'avertissements et d'alertes liées aux états et aux performances. Pour plus d’informations, consultez [définition des seuils et des avertissements dans le moniteur de réplication](../../../relational-databases/replication/monitor/set-thresholds-and-warnings-in-replication-monitor.md). Vous pouvez aussi définir des alertes pour d'autres événements de réplication à l'aide de l'infrastructure d'alertes de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [créer un événement défini par l’utilisateur](../../../ssms/agent/create-a-user-defined-event.md).  
  
### Pour configurer une alerte de réplication prédéfinie dans Management Studio  
  
1.  Connectez-vous au serveur de distribution dans [!INCLUDE[ssManStudio](../../../includes/ssmanstudio-md.md)], puis développez le nœud du serveur.  
  
2.  Développez le **l’Agent SQL Server** dossier, puis développez le **alertes** dossier.  
  
3.  Cliquez sur une alerte de réplication, puis cliquez sur **propriétés**.  
  
4.  Définir les options dans la **\< Nom_alerte> des propriétés d’alertes** boîte de dialogue :  
  
    -   Sur la page **Général** , cliquez sur **Activer**; spécifiez la base de données à laquelle l'alerte doit s'appliquer.  
  
    -   Sur le **réponse** spécifiez si un message électronique doit être envoyé et/ou une tâche doit être exécutée.  
  
         Si l’alerte est **réplication : Échec de la validation de données par l’abonné**, vous pouvez spécifier le travail de réponse que la réplication fournit pour cette alerte : sélectionnez **exécuter le travail**, puis cliquez sur le bouton Parcourir (**...**). Dans la **localiser le travail** boîte de dialogue, cliquez sur **Parcourir**. Dans la **Rechercher des objets** boîte de dialogue, sélectionnez **Réinitialiser les abonnements présentant des erreurs de validation de données**. Cliquez sur **OK** dans les deux boîtes de dialogue ouvertes. Lorsque le travail s'exécute, il utilise un appel de procédure distante (RPC) à une procédure stockée qui réinitialise l'abonnement. Si le serveur de publication utilise un serveur de distribution distant, vous devez définir une connexion serveur distante sur le serveur de publication, pour que l'appel de procédure distante puisse être effectué du serveur de distribution au serveur de publication.  
  
    -   Sur la page **Options** , personnalisez le texte de la réponse.  
  
5.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
### Pour configurer une alerte de seuil dans le moniteur de réplication  
  
1.  Sur le **avertissements** onglet, cliquez sur **configurer les alertes**.  
  
2.  Dans la boîte de dialogue **Configurer des alertes de réplication** , sélectionnez une alerte puis cliquez sur **Configurer**.  
  
3.  Définir les options dans la **\< Nom_alerte> des propriétés d’alertes** boîte de dialogue :  
  
    -   Sur la page **Général** , cliquez sur **Activer**; spécifiez la base de données à laquelle l'alerte doit s'appliquer.  
  
    -   Sur le **réponse** spécifiez si un message électronique doit être envoyé et/ou une tâche doit être exécutée.  
  
         Si l’alerte est **réplication : Échec de la validation de données par l’abonné**, vous pouvez spécifier le travail de réponse que la réplication fournit pour cette alerte : sélectionnez **exécuter le travail**, puis cliquez sur le bouton Parcourir (**...**). Dans la **localiser le travail** boîte de dialogue, cliquez sur **Parcourir**. Dans la **Rechercher des objets** boîte de dialogue, sélectionnez **Réinitialiser les abonnements présentant des erreurs de validation de données**. Cliquez sur **OK** dans les deux boîtes de dialogue ouvertes. Lorsque le travail s'exécute, il utilise un appel de procédure distante (RPC) à une procédure stockée qui réinitialise l'abonnement. Si le serveur de publication utilise un serveur de distribution distant, vous devez définir une connexion serveur distante sur le serveur de publication, pour que l'appel de procédure distante puisse être effectué du serveur de distribution au serveur de publication.  
  
    -   Sur la page **Options** , personnalisez le texte de la réponse.  
  
4.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
5.  Cliquez sur **Fermer**.  
  
## Voir aussi  
 [Utiliser les alertes pour les événements des agents de réplication](../../../relational-databases/replication/agents/use-alerts-for-replication-agent-events.md)  
  
  