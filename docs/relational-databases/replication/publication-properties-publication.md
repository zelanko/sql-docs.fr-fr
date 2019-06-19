---
title: Réplication SQL Server, boîte de dialogue Propriétés de la publication | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
f1_keywords:
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
- sql13.rep.newpubwizard.pubproperties.agentsecurity.f1
- sql13.rep.newpubwizard.pubproperties.filterrows.f1
- sql13.rep.newpubwizard.pubproperties.internetsynchronization.f1
- sql13.rep.newpubwizard.pubproperties.general.f1
- sql13.rep.newpubwizard.pubproperties.publicationaccesslist.f1
- sql13.rep.newpubwizard.pubproperties.snapshotformat.f1
helpviewer_keywords:
- Publication Properties dialog box
ms.assetid: 66e845e9-1308-4288-9110-ad2f22f1fc58
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: da86b20dba26536626010d14c1f81a1bbd852156
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "65620368"
---
# <a name="sql-server-replication-publication-properties--dialog-box"></a>Réplication SQL Server, boîte de dialogue Propriétés de la publication
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]

Cette page décrit les pages disponibles dans la boîte de dialogue Propriétés de la publication. 

## <a name="general"></a>Général
 La page **Général** de la boîte de dialogue **Propriétés de la publication** contient des informations générales sur la publication, notamment le nom, la description et la stratégie d'expiration d'abonnement.  
  
### <a name="options"></a>Options  
 **Name**  
 Nom de la publication (en lecture seule).  
  
 **Sauvegarde de la base de données**  
 Nom de la base de données de publication (en lecture seule).  
  
 **Description**  
 Description de la publication.  
  
 **Type**  
 Type de la publication (en lecture seule).  
  
 **Expiration de l'abonnement**  
 Sélectionnez l'une des options d'expiration d'abonnement : **Les abonnements n’expirent jamais** ou **Les abonnements expirent** avec une période explicite (**Intervalle**).  
  
 Pour les publications d'instantané et transactionnelles, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'accepter la valeur par défaut **Les abonnements n'expirent jamais**.  
  
 Pour la réplication de fusion, [!INCLUDE[msCoName](../../includes/msconame-md.md)] recommande d'accepter la valeur par défaut **Les abonnements expirent** et de définir une valeur aussi basse que possible pour l' **intervalle**. Lorsque la période d'expiration d'abonnement augmente, le volume des métadonnées stockées augmente également, ce qui peut affecter les performances. Déterminez la nécessité de déconnecter les abonnés ou simplement de ne pas les synchroniser pendant une longue période par rapport aux problèmes de performance associés au stockage et au traitement d'un gros volume de métadonnées.  
  
 Pour plus d’informations, voir [Subscription Expiration and Deactivation](../../relational-databases/replication/subscription-expiration-and-deactivation.md).  
  
 **Niveau de compatibilité**  
 [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures uniquement. Publications de fusion uniquement. Sélectionnez la version minimale [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] nécessaire aux abonnés qui se synchronisent avec cette publication. Il existe des règles permettant de déterminer le niveau de compatibilité.  

## <a name="filter-rows"></a>Filtrer les lignes
  La page **Filtrer les lignes** de la boîte de dialogue **Propriétés de la publication** vous permet d'ajouter, de modifier ou de supprimer :  
  
-   Permet d'appliquer des filtres de lignes statiques à des articles de table dans des publications d'instantané, transactionnelles et de fusion.   
-   Permet d'appliquer des filtres de lignes paramétrés à des articles de table dans des publications de fusion.    
-   Utilisez les filtres de jointure afin d'étendre les filtres des articles de table de fusion aux articles de table associés. Pour plus d’informations sur les options de filtrage, consultez [Filtrer des données publiées](../../relational-databases/replication/publish/filter-published-data.md).  
  
> [!NOTE]  
>  L'ajout, la modification ou la suppression d'un filtre nécessite un instantané pour la publication et requiert que tous les abonnements soient réinitialisés.  
  
Pour accroître au maximum les performances de votre application et réduire le stockage distant nécessaire, ou pour limiter la disponibilité de certaines données à des abonnés spécifiques, vous pouvez publier uniquement les données requises. Une publication peut comporter simultanément des tables filtrées et non filtrées. Par exemple, vous pouvez inclure l'intégralité de la table des produits de l'entreprise (non filtrée) et utiliser les filtres de lignes pour générer une table filtrée des clients d'une région particulière. En filtrant les données publiées, vous pouvez :  
  
-   Réduire la quantité de données envoyées via le réseau.    
-   Réduire la quantité d’espace de stockage requis sur l’abonné.    
-   Personnaliser les publications et les applications en fonction des exigences des abonnés individuels.    
-   Éviter ou réduire les conflits lorsque les abonnés mettent à jour les données car différentes partitions de données peuvent être envoyées vers différents abonnés (deux abonnés ne mettent pas à jour les mêmes valeurs de données).    
-   Éviter de transmettre des données sensibles. Vous pouvez utiliser les filtres de lignes et de colonne pour limiter l'accès d'un abonné aux données. Pour les réplications de fusion, vous devez tenir compte de certains points de sécurité si vous utilisez un filtre paramétré qui inclut HOST_NAME(). Pour plus d'informations, consultez la section « Filtrage avec HOST_NAME() » dans [Parameterized Row Filters](../../relational-databases/replication/merge/parameterized-filters-parameterized-row-filters.md).  
  
### <a name="options"></a>Options  
 **Tables filtrées**  
 Ce volet est rempli avec des filtres à mesure que vous les ajoutez aux articles de table dans la publication. Les tables avec filtres de lignes sont affichées en tant que nœuds de niveau supérieur dans le volet. Pour les publications de fusion, les tables auxquelles les filtres ont été étendus par le biais d'un filtre de jointure sont affichées en tant que nœuds enfants.  
  
 **Ajouter**  
 Cliquez sur **Ajouter** pour lancer une boîte de dialogue qui vous permet de filtrer les articles de table. Si vous cliquez sur **Ajouter** pour une publication d'instantané ou transactionnelle, une boîte de dialogue s'ouvre immédiatement. Si vous cliquez sur **Ajouter** pour une publication de fusion, trois choix s’affichent : **Ajouter un filtre**, **Ajouter une jointure pour étendre le filtre sélectionné** et **Générer automatiquement des filtres**.  
  
-   Sélectionnez **Ajouter un filtre** pour ouvrir la boîte de dialogue du **même nom** . Elle vous permet d'appliquer des filtres de lignes à un article de table. Dans la boîte de dialogue **Ajouter un filtre** , vous pouvez, par exemple, indiquer qu'une table contenant des données client doit uniquement comporter des données relatives aux clients français lors de sa réplication vers des abonnés.  
  
-   Sélectionnez **Ajouter une jointure pour étendre le filtre sélectionné** afin de lancer la boîte de dialogue **Ajouter une jointure** . La boîte de dialogue **Ajouter une jointure** vous permet d'étendre un filtre de lignes de sorte à filtrer les données dans les tables associées à la table contenant le filtre de ligne. Par exemple, si une table de clients est filtrée de manière à ne contenir que les données relatives aux clients français et qu'une table de commandes client lui est associée, vous pouvez définir une jointure entre les deux tables afin que la table de commandes inclue uniquement les commandes émanant de clients français.  
  
    > [!NOTE]  
    >  Cette option est uniquement disponible si vous sélectionnez d'abord la table de base de la jointure dans le volet du filtre.  
  
-   Sélectionnez **Générer automatiquement des filtres** pour ouvrir la boîte de dialogue **Générer des filtres** . Cette boîte de dialogue vous permet de définir un filtre de lignes pour une table dans une publication de fusion afin que la réplication s'étende automatiquement aux autres tables associées par le biais de relations de clés étrangères. Par exemple, une publication peut inclure trois tables : une table de clients, une table de commandes (avec une clé étrangère pour la table de clients) et une table avec les détails des commandes (avec une clé étrangère pour la table de commandes). Définissez un filtre de lignes pour la table client afin que la réplication s'étende aux autres tables.  
  
    > [!NOTE]  
    >  Lorsque les filtres sont générés automatiquement par réplication, tous les filtres existants dans la publication sont supprimés. Pour inclure les filtres générés automatiquement et ceux définis manuellement, commencez par générer des filtres. Vous pouvez uniquement spécifier un jeu de filtres générés automatiquement pour chaque publication.  
  
 **Modifier**  
 Sélectionnez un filtre de lignes ou de jointure dans le volet des filtres et cliquez sur **Modifier** pour ouvrir la boîte de dialogue **Modifier le filtre** ou **Modifier une jointure** .  
  
 **Supprimer**  
 Sélectionnez un filtre de lignes ou de jointure dans le volet des filtres et cliquez sur **Supprimer** pour supprimer le filtre.  
  
 **Rechercher une table**  
 Publications de fusion uniquement. Cliquez sur **Rechercher une table** pour trouver une table dans une arborescence de filtres complexe. Dans une base de données comportant des relations complexes, une table peut être jointe à plusieurs tables et apparaître dès lors à plusieurs endroits dans l'arborescence des filtres.  
  
 La table réelle apparaît à un seul endroit dans l'arborescence. Aux autres endroits, elle est représentée par un raccourci. Ce raccourci n'est qu'une référence à la table ; il n'affiche pas les nœuds enfants de la table. Un nœud de raccourci est identifié par une flèche. En développant ce nœud, vous affichez le texte **Cliquez sur Rechercher une table pour afficher la table de \<nom_table>**.  
  
 Sélectionnez un nœud de raccourci dans le volet et cliquez sur **Rechercher une table** . Le volet se développe et la table apparaît en surbrillance. Si vous cliquez sur **Rechercher une table** sans sélectionner un nœud de raccourci, une boîte de dialogue **Rechercher une table** s'ouvre.  
  
 **Filter**  
 Contient la définition [!INCLUDE[tsql](../../includes/tsql-md.md)] du filtre sélectionné dans le volet.  

## <a name="publication-access-list"></a>Liste d'accès aux publications (PAL)
  La page **Liste d'accès aux publications** de la boîte de dialogue **Propriétés de la publication** vous permet d'ajouter et de supprimer des informations de connexion, des comptes et des groupes de la liste d'accès aux publications. Cette dernière constitue le mécanisme principal assurant la sécurité du serveur de publication. Lorsque vous créez une publication, la réplication crée une liste d'accès aux publications pour cette première. Cette liste, fonctionnant de la même façon qu'une liste de contrôle d'accès [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows, contient une liste d'informations de connexions, de comptes et de groupes bénéficiant de l'autorisation d'accès à la publication.  
  
 Lorsqu'un Abonné se connecte au serveur de publication ou au serveur de distribution pour demander l'accès à la publication, ses informations de connexion sont comparées aux informations d'authentification contenues dans la liste d'accès aux publications. Ceci permet d'assurer un niveau de sécurité supplémentaire vis-à-vis du serveur de publication en empêchant l'utilisation des informations de connexion du serveur de publication et du serveur de distribution par un outil client pouvant procéder à des modifications directement sur le serveur de publication. Pour plus d’informations, consultez [Sécuriser le serveur de publication](../../relational-databases/replication/security/secure-the-publisher.md).  
  
### <a name="options"></a>Options  
 **Ajouter**  
 Permet d'ajouter une nouvelle entrée à la liste. Vous ne pouvez ajouter que les noms de connexion, de compte ou de groupe déjà définis aussi bien sur le serveur de publication que le serveur de distribution. Ils sont par ailleurs définis sur ces deux serveurs si les comptes du domaine sont utilisés ou si des comptes locaux ont été créés sur les deux serveurs.  
  
 **Supprimer**  
 Supprime de la liste l'entrée sélectionnée.  
  
 **Supprimer tout**  
 Supprime toutes les entrées de la liste.  

## <a name="ftp-snapshot-and-internet"></a>Instantané FTP et Internet

-   définir les propriétés d'envoi de l'instantané via FTP (File Transfer Protocol). Pour plus d’informations, consultez [Remettre un instantané par le biais du protocole FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md). Pour utiliser FTP afin d'envoyer un instantané, vous devez définir un serveur FTP. Consultez la documentation [!INCLUDE[msCoName](../../includes/msconame-md.md)] Windows pour plus d'informations.  
  
    > [!NOTE]  
    >  Les modifications des paramètres FTP nécessitent de générer un nouvel instantané.  
  
-   Définissez les propriétés de synchronisation Web de la réplication de fusion sur [!INCLUDE[ssVersion2005](../../includes/ssversion2005-md.md)] et versions ultérieures qui permet de synchroniser les abonnements sur HTTPS (Secure Hypertext Transfer Protocol). Pour utiliser la synchronisation Web, vous devez configurer un serveur IIS ( [!INCLUDE[msCoName](../../includes/msconame-md.md)] Internet Information Services). Pour plus d’informations, consultez [Web Synchronization for Merge Replication](../../relational-databases/replication/web-synchronization-for-merge-replication.md).  
  
### <a name="options"></a>Options  
 **Accéder aux fichiers d'instantanés via FTP**  
 Sélectionnez **Autoriser les abonnés à télécharger des fichiers d'instantanés via le protocole FTP (File Transfer Protocol)** et spécifiez le **nom du serveur FTP**, le **numéro de port**, **le chemin d'accès depuis le dossier racine FTP**, la **connexion**et le **mot de passe**pour permettre aux abonnés d'utiliser FTP pour l'envoi d'instantanés.  
  
 Cette option permet aux abonnés d'utiliser FTP pour extraire les fichiers d'instantanés, mais elle ne les oblige pas à le faire. Si vous sélectionnez cette option, l'Assistant Nouvel abonnement amène par défaut les abonnés à extraire les fichiers d'instantanés via FTP. Pour changer ce paramètre, utilisez la boîte de dialogue **Propriétés de l'abonnement** . Si vous autorisez les abonnés à accéder aux fichiers d'instantanés via FTP, définissez le dossier FTP comme emplacement de stockage des fichiers d'instantanés dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication** . Dans ce cas, l'Agent d'instantané met à jour automatiquement les fichiers du dossier FTP lorsqu'un nouvel instantané est généré. Si l'emplacement ne correspond pas au dossier FTP, vous devez mettre à jour les fichiers manuellement lorsqu'un nouvel instantané est généré. Pour plus d’informations, consultez [Remettre un instantané via FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
 **Synchronisation Web**  
 Réplication de fusion uniquement. Sélectionnez **Autoriser les abonnés à se synchroniser en se connectant à un serveur Web**et définissez une adresse de serveur Web pour permettre aux abonnés d'utiliser la synchronisation Web. Le serveur web doit utiliser le protocole SSL (Secure Sockets Layer) et l’adresse web doit être complète, par exemple `https://server.domain.com/synchronize`. Pour plus d’informations, consultez [Configurer la synchronisation Web](../../relational-databases/replication/configure-web-synchronization.md).  


## <a name="agent-security"></a>Sécurité de l’agent
  La page **Sécurité de l'agent** de la boîte de dialogue **Propriétés de la publication** vous permet d'accéder aux paramètres des comptes sous lesquels s'exécutent les agents ci-après. Elle vous permet également d'établir des connexions aux ordinateurs dans une topologie de réplication :  
  
-   Agent d'instantané pour toutes les publications ;  
  
-   Agent de lecture du journal pour toutes les publications transactionnelles ; Il existe un Agent de lecture du journal pour chaque base de données publiée en vue de la réplication transactionnelle. La modification des paramètres de l'Agent de lecture du journal affecte toutes les publications transactionnelles dans une base de données.  
  
-   l'Agent de lecture de la file d'attente propre aux publications transactionnelles autorisant les abonnements de mise à jour dans la file d'attente ; Il existe un Agent de lecture de la file d'attente pour chaque base de données de distribution. La modification des paramètres de l'Agent de lecture de la file d'attente affecte toutes les publications transactionnelles avec des abonnements mis à jour en attente qui utilisent la même base de données de distribution. Pour plus d’informations sur les paramètres de sécurité de l’Agent de lecture de la file d’attente, consultez [Afficher et modifier les paramètres de sécurité de la réplication](../../relational-databases/replication/security/view-and-modify-replication-security-settings.md).  
  
 Pour plus d'informations sur les paramètres de sécurité et les autorisations requis par chaque agent, consultez [Replication Agent Security Model](../../relational-databases/replication/security/replication-agent-security-model.md).  
  
### <a name="options"></a>Options  
 **Paramètres de sécurité** ou **Créer un Agent**  
 Si un travail d'agent a été créé, cliquez sur **Paramètres de sécurité** pour accéder à une boîte de dialogue qui vous permet de modifier les paramètres de sécurité d'un agent. Dans le cas contraire, cliquez sur **Créer un Agent** pour en créer un et spécifier les paramètres de sécurité.  

## <a name="data-partitions"></a>Partitions de données
Partitions de données  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]  
  La page **Partitions de données** de la boîte de dialogue **Propriétés de la publication** permet de définir des partitions de données pour les publications de fusion qui utilisent le filtrage paramétré. Après avoir défini les partitions, vous pouvez générer des instantanés pour fournir différents jeux de données initiaux pour différents abonnés en fonction des propriétés de connexion (connexion et/ou nom d'ordinateur) des abonnés. Vous pouvez également permettre aux abonnés de demander la distribution et la génération d'instantanés s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois. Pour plus d'informations, voir [Créer un instantané d'une publication de fusion avec des filtres paramétrés](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
### <a name="options"></a>Options  
 **Ajouter**  
 Cliquez sur **Ajouter** pour définir une partition. Dans la boîte de dialogue **Ajouter une partition de données** , définissez les valeurs de **HOST_NAME()** et/ou de **SUSER_SNAME()** et spécifiez une planification d'actualisation des instantanés.  
  
 **Modifier**  
 Sélectionnez une partition existante dans la grille et cliquez sur **Modifier** pour modifier la partition.  
  
 **Supprimer**  
 Sélectionnez une partition existante dans la grille et cliquez sur **Supprimer** pour supprimer la partition.  
  
 **Générer les instantanés sélectionnés maintenant**  
 Sélectionnez une ou plusieurs partitions dans la grille et cliquez sur **Générer les instantanés sélectionnés maintenant** pour générer des instantanés pour ces partitions.  
  
 **Nettoyer les instantanés existants**  
 Sélectionnez une ou plusieurs partitions dans la grille et cliquez sur **Nettoyer les instantanés existants** pour nettoyer les instantanés pour ces partitions.  
  
 **Définir automatiquement une partition et générer un instantané si nécessaire lorsqu'un nouvel abonné essaie de se synchroniser**  
 Sélectionnez cette option si vous voulez permettre aux abonnés de demander la génération et l'application d'instantanés. Les abonnés peuvent avoir besoin de cette option s'ils ne disposent pas d'un instantané pour leur partition lorsqu'ils se synchronisent pour la première fois.  

## <a name="snapshot"></a>Snapshot
Snapshot  
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]  
  La page **Instantané** de la boîte de dialogue **Propriétés de la publication** permet de définir un format d'instantané, l'emplacement d'un dossier d'instantanés et des scripts avant et après l'application d'instantané. Le dossier d'instantanés doit être défini comme partage et disposer des autorisations suffisantes pour les agents qui lisent et écrivent des fichiers dans le dossier. Pour plus d’informations sur une sécurisation appropriée du dossier, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
> [!NOTE]  
>  Les modifications nécessitent un nouvel instantané pour la publication. Pour plus d’informations, consultez [Modifier les propriétés des publications et des articles](../../relational-databases/replication/publish/change-publication-and-article-properties.md).  
  
### <a name="options"></a>Options  
 **Format d'instantané**  
 Sélectionnez le mode natif ou le mode caractère pour le format d'instantané.  
  
-   Sélectionnez **SQL Server natif - tous les Abonnés doivent être des serveurs qui exécutent SQL Server** si tous les abonnés sont des instances de [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] autres que [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssEW](../../includes/ssew-md.md)]. Le format natif d'instantané fournit les meilleures performances.    
-   Sélectionnez **Caractère - obligatoire si un serveur de publication ou un Abonné n'exécute pas SQL Server** si des abonnés exécutent [!INCLUDE[ssEW](../../includes/ssew-md.md)] ou sont des abonnés non-[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] .    
 **Emplacement des fichiers d'instantané**  
 Sélectionnez l'emplacement des fichiers d'instantané. Vous pouvez les stocker dans l'emplacement par défaut et dans un emplacement différent, ou seulement dans un emplacement différent. Les fichiers stockés dans un emplacement différent peuvent être compressés.  
  
-   Sélectionnez **Placer les fichiers dans le dossier par défaut** pour utiliser le dossier d'instantanés du serveur de publication. L'emplacement du dossier d'instantanés est en lecture seule dans cette boîte de dialogue, car il ne peut être changé que dans la boîte de dialogue **Propriétés du serveur de distribution** du serveur de publication. Pour plus d’informations, consultez [Modifier les propriétés des instantanés](../../relational-databases/replication/snapshot-options.md).    
-   Sélectionnez **Placer les fichiers dans le dossier suivant** pour remplacer l'emplacement par défaut ou ajouter un emplacement. Tapez le chemin d'accès dans la zone de texte ou cliquez sur **Parcourir** et accédez à un emplacement. Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier** pour compresser les fichiers dans l'autre emplacement d'instantanés. L'emplacement secondaire peut se trouver sur un autre serveur, un lecteur réseau ou un support amovible (tel qu'un CD-ROM ou un disque amovible). Pour plus d’informations, consultez [Modifier les propriétés des instantanés](../../relational-databases/replication/snapshot-options.md).  
  
 **Exécuter des scripts supplémentaires**  
 Définissez les scripts à exécuter avant et après l'application de l'instantané au niveau de l'Abonné. Vous ne pouvez pas définir de scripts si le **format d'instantané** est **Caractère**.  
  
 Les scripts sont facultatifs, mais ils fournissent une méthode simple pour exécuter des commandes et appliquer des modifications administratives au niveau des abonnés. Pour plus d’informations sur l’exécution des scripts, consultez [Exécuter des scripts avant et après l’application de l’instantané](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).  
  
-   Entrez un chemin dans la zone de texte **Exécuter ce script avant l'application de l'instantané** ou cliquez sur **Parcourir** pour définir l'emplacement du script.    
-   Entrez un chemin dans la zone de texte **Exécuter ce script après l'application de l'instantané** ou cliquez sur **Parcourir** pour définir l'emplacement du script. 
  
## <a name="see-also"></a> Voir aussi  
 [Create a Publication](../../relational-databases/replication/publish/create-a-publication.md)   
 [Afficher et modifier les propriétés d’une publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md)   
 [Publier des données et des objets de base de données](../../relational-databases/replication/publish/publish-data-and-database-objects.md)   

  
  
