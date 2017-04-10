---
title: "Propri&#233;t&#233;s de l&#39;abonnement - Abonn&#233; | Microsoft Docs"
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
  - "sql13.rep.newsubwizard.subproperties.subscriber.f1"
helpviewer_keywords: 
  - "boîte de dialogue Propriétés de l'abonnement"
ms.assetid: bef66929-3234-4a45-8ec4-3b271519d07a
caps.latest.revision: 25
author: "BYHAM"
ms.author: "rickbyh"
manager: "jhubbard"
caps.handback.revision: 25
---
# Propri&#233;t&#233;s de l&#39;abonnement - Abonn&#233;
  Le **Propriétés d’un abonnement** boîte de dialogue sur l’abonné permet d’afficher et définir des propriétés pour les abonnements extraits.  
  
 Chaque propriété de la **Propriétés d’un abonnement** boîte de dialogue comporte une description. Cliquez sur une propriété pour afficher sa description au bas de la boîte de dialogue. Cette rubrique fournit des informations sur diverses propriétés, Les propriétés sont regroupées selon les catégories suivantes :  
  
-   Propriétés appliquées à tous les abonnements.  
  
-   Propriétés appliquées aux abonnements transactionnels.  
  
-   Propriétés appliquées aux abonnements de fusion.  
  
 Si une option est affichée en lecture seule, vous pouvez la configurer uniquement lorsque l'abonnement est créé. Si vous voulez configurer des options non disponibles dans l'Assistant Nouvel abonnement, créez l'abonnement avec des procédures stockées. Pour plus d'informations, consultez [Create a Pull Subscription](../../relational-databases/replication/create-a-pull-subscription.md) et [Create a Push Subscription](../../relational-databases/replication/create-a-push-subscription.md).  
  
> [!NOTE]  
>  Si un Agent de distribution ou un Agent de fusion n'est pas encore créé pour l'abonnement, de nombreuses propriétés ne sont pas affichées. Pour créer un travail d’agent pour un abonnement par extraction de données, exécutez [sp_addpullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addpullsubscription-agent-transact-sql.md) (pour un abonnement à une publication transactionnelle ou de capture instantanée) ou [sp_addmergepullsubscription_agent & #40 ; Transact-SQL & #41 ;](../../relational-databases/system-stored-procedures/sp-addmergepullsubscription-agent-transact-sql.md) (pour un abonnement à une publication de fusion).  
  
## Options pour tous les abonnements  
 **Initialise les données publiées à partir d'un instantané**  
 Détermine si les options sont initialisées avec un instantané (par défaut) ou une autre méthode. Pour plus d’informations sur l’initialisation des abonnements, consultez [initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md).  
  
 **Emplacement de l'instantané**  
 Détermine l'emplacement à partir duquel les fichiers d'instantanés sont accessibles lors de l'initialisation ou de la réinitialisation de l'abonnement. Les valeurs suivantes peuvent déterminer l'emplacement :  
  
-   **Emplacement par défaut**: l’emplacement par défaut, qui est défini lors de la configuration d’un serveur de distribution. Pour plus d’informations, consultez [spécifier l’emplacement par défaut des instantanés & #40 ; SQL Server Management Studio & #41 ;](../../relational-databases/replication/specify-the-default-snapshot-location-sql-server-management-studio.md).  
  
-   **Autre dossier**: un autre emplacement, ce qui peut être spécifié dans le **Propriétés de la Publication** boîte de dialogue. Pour plus d’informations, consultez [autres emplacements de dossier de capture instantanée](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   **Dossier de capture instantanée dynamique**: un emplacement de capture instantanée pour les publications de fusion qui utilisent des filtres de lignes paramétrable. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/snapshots-for-merge-publications-with-parameterized-filters.md).  
  
-   **Dossier FTP**: un dossier accessible à un serveur de transfert de protocole FTP (File). Pour plus d’informations, consultez [instantanés via FTP Transfer](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
 **Dossier d'instantanés**  
 Si vous sélectionnez une valeur autre que **emplacement par défaut** pour la **emplacement de l’instantané** option, vous devez spécifier un chemin d’accès au dossier de capture instantanée.  
  
 **Utiliser le Gestionnaire de synchronisation Windows**  
 Détermine s'il est possible de synchroniser l'abonnement à l'aide du Gestionnaire de synchronisation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows.  
  
 **Sécurité**  
 Cliquez sur le **compte de processus de l’Agent** de ligne, puis cliquez sur le bouton des propriétés (**...**) pour modifier le compte sous lequel l’Agent de Distribution ou l’Agent de fusion s’exécute sur l’abonné. Les options de sécurité des connexions dépendent du type d'abonnement :  
  
-   Pour les abonnements à une publication transactionnelle : pour modifier le compte sous lequel l’Agent de Distribution établit des connexions au serveur de distribution, cliquez sur **connexion du serveur de distribution**, puis cliquez sur le bouton des propriétés (**...**).  
  
-   Pour les abonnements de mise à jour immédiate à une publication transactionnelle : outre la connexion de serveur de distribution décrite ci-dessus, vous pouvez modifier la méthode utilisée pour propager les modifications de l’abonné vers le serveur de publication : cliquez sur **connexion éditeur**, puis cliquez sur le bouton des propriétés (**...**).  
  
-   Pour les abonnements aux publications de fusion, cliquez sur **connexion éditeur**, puis cliquez sur le bouton des propriétés (**...**).  
  
 Pour plus d’informations sur les autorisations requises pour chaque agent, consultez [modèle de sécurité de l’Agent de réplication](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
## Options des abonnements transactionnels  
 **Abonnement pouvant être mis à jour**  
 Détermine si les modifications de l'Abonné sont répliquées dans le serveur de publication. Vous pouvez répliquer les modifications en utilisant la mise à jour immédiate ou en file d'attente. L’option **méthode de mise à jour d’abonnés** détermine la méthode à utiliser. Pour plus d’informations, consultez la page [à des abonnements pour la réplication transactionnelle](../../relational-databases/replication/transactional/updatable-subscriptions-for-transactional-replication.md).  
  
## Options des abonnements de fusion  
 **Définition de la partition (HOST_NAME)**  
 Pour une publication qui utilise des filtres paramétrés, la réplication de fusion évalue une des deux fonctions système (ou les deux si le filtre fait référence aux deux) pendant la synchronisation pour déterminer les données qu’un abonné doit recevoir : **SUSER_SNAME()** ou **HOST_NAME()**. Par défaut, **HOST_NAME()** retourne le nom de l’ordinateur sur lequel l’Agent de fusion est en cours d’exécution, mais vous pouvez remplacer cette valeur dans l’Assistant Nouvel abonnement. Pour plus d’informations sur les filtres paramétrés et en remplaçant **HOST_NAME()**, consultez la page [les filtres de lignes paramétrable](../../relational-databases/replication/merge/parameterized-row-filters.md).  
  
 **Type d’abonnement** et **priorité**  
 Indique si l'abonnement est un abonnement de client ou de serveur (cette option n'est pas modifiable après la création de l'abonnement). Les abonnements de serveur peuvent republier les données vers d'autres abonnés. Il est possible de leur affecter une priorité pour la résolution des conflits.  
  
 Si vous avez sélectionné un abonnement de type serveur dans l'Assistant Nouvel abonnement, l'abonné a la priorité utilisée lors de la résolution des conflits.  
  
 **Résoudre les conflits interactivement**  
 Détermine s'il faut utiliser l'interface utilisateur du Résolveur interactif pour résoudre les conflits pendant la synchronisation de fusion. Cela requiert une valeur de **Activer** pour **utiliser le Gestionnaire de synchronisation Windows**. Pour plus d’informations, consultez [Interactive Conflict Resolution](../../relational-databases/replication/merge/interactive-conflict-resolution.md).  
  
 **Synchronisation Web**  
 **Utiliser la synchronisation Web** détermine s’il faut se connecter à un [!INCLUDE[msCoName](../../includes/msconame-md.md)] serveur Internet Information Services (IIS) pour synchroniser l’abonnement. Cette option est disponible uniquement si la publication est activée pour la synchronisation. Pour plus d’informations, voir [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
 Si vous sélectionnez **True** pour **utiliser la synchronisation Web**:  
  
-   Entrez l’adresse complète du serveur IIS dans **adresse de serveur Web**.  
  
-   Cliquez sur le **connexion au serveur Web** de ligne, puis cliquez sur le bouton des propriétés (**...**) pour définir ou modifier le compte sous lequel l’abonné se connecte au serveur IIS.  
  
-   Modification **délai d’attente du serveur Web** si nécessaire. Ce délai d'attente représente le temps (en secondes) écoulé avant l'expiration d'une demande de synchronisation Web.  
  
 Pour plus d’informations sur la configuration, consultez la page [configurer la synchronisation Web](../../relational-databases/replication/configure-web-synchronization.md).  
  
## Voir aussi  
 [View and Modify Pull Subscription Properties](../../relational-databases/replication/view-and-modify-pull-subscription-properties.md)   
 [View and Modify Push Subscription Properties](../../relational-databases/replication/view-and-modify-push-subscription-properties.md)   
 [S'abonner à des publications](../../relational-databases/replication/subscribe-to-publications.md)  
  
  