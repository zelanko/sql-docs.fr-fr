---
title: Modifier les options d’initialisation d’instantané
description: Modifiez différentes options d’initialisation d’instantané de réplication telles que le format d’instantané et l’emplacement du dossier d’instantanés dans SQL Server Management Studio.
ms.custom: seo-lt-2019
ms.date: 11/20/2018
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 9d44a77a95b8b6a46fbc37a21a8abbd5ee75dfce
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287151"
---
# <a name="modify-snapshot-initialization-options-for-sql-replication"></a>Modifier les options d’initialisation d’instantané pour la réplication SQL 
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]

Il existe un certain nombre d’options pour spécifier quand [initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md).

## <a name="specify-snapshot-format-sql-server-management-studio"></a>spécifier le format d'instantané (SQL Server Management Studio)
  Spécifiez le format d’instantané dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-specify-snapshot-format"></a>Pour spécifier le format d'instantané  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez **SQL Server natif - tous les Abonnés doivent être des serveurs qui exécutent SQL Server** ou **Caractère - obligatoire si un serveur de publication ou un Abonné n’exécute pas SQL Server**.  
  
    > [!NOTE]  
    >  Il est conseillé de sélectionner le format natif, à moins que cette publication ne doive prendre en charge les abonnements à une base de données SQL Server ou à une base de données non-SQL Server.  
  
2.  Sélectionnez **OK**.   

## <a name="snapshot-folder-locations"></a>Emplacements du dossier d’instantanés

### <a name="default-snapshot-location"></a>Emplacement par défaut des instantanés
Spécifiez l'emplacement par défaut des instantanés dans la page **Dossier d'instantanés** de l'Assistant Configuration de la distribution. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Configurer la publication et la distribution](../../relational-databases/replication/configure-publishing-and-distribution.md). Si vous créez une publication sur un serveur qui n'est pas configuré en tant que serveur de distribution, spécifiez un emplacement d'instantanés par défaut dans la page **Dossier d'instantanés** de l'Assistant Nouvelle publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Créer une publication](../../relational-databases/replication/publish/create-a-publication.md).  
  
 Modifiez l’emplacement par défaut des instantanés dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>** . Pour plus d’informations, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](../../relational-databases/replication/view-and-modify-distributor-and-publisher-properties.md). Définissez le dossier d’instantanés pour chaque publication dans la boîte de dialogue **Propriétés de publication - \<Publication>** . Pour plus d'informations, voir [View and Modify Publication Properties](../../relational-databases/replication/publish/view-and-modify-publication-properties.md).  
  
### <a name="to-modify-the-default-snapshot-location"></a>Pour modifier l'emplacement par défaut des instantanés  
  
1.  Dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>** , cliquez sur le bouton des propriétés ( **…** ) du serveur de publication pour lequel vous voulez modifier l’emplacement par défaut des captures instantanées.    
2.  Dans la boîte de dialogue **Propriétés du serveur de publication - \<Serveur de publication>** , entrez une valeur pour la propriété **Dossier des captures instantanées par défaut**.  
  
    > [!NOTE]  
    >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).    
3.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
 

### <a name="alternate-snapshot-locations"></a>Autres emplacements d’instantanés
Les autres emplacements d'instantané vous permettent de stocker les fichiers d'instantanés dans un lieu autre que l'emplacement par défaut (généralement, sur le serveur de distribution), ou s'ajoutent à cet emplacement par défaut. Il peut s'agir d'un autre serveur, d'un lecteur réseau ou d'un support amovible tel qu'un CD-ROM ou un disque.  
  
L'autre emplacement d'instantané est mémorisé sous la forme d'une propriété de la publication. Dans la mesure où cet emplacement est une propriété de la publication, l'Agent de distribution et l'Agent de fusion sont capables de déterminer l'instantané approprié dans le cadre du processus de synchronisation.  
  
Si vous souhaitez spécifier un autre emplacement pour le dossier d'instantanés ou compresser des fichiers d'instantanés, créez la publication sans créer immédiatement l'instantané initial, définissez les propriétés de publication de l'emplacement de l'instantané, puis exécutez l'Agent d'instantané pour cette publication. Si vous changez l'autre emplacement après avoir créé l'instantané initial, les instantanés déjà générés pour la publication ne seront pas transférés vers le nouvel emplacement. Dans ce cas, et en fonction des paramètres de publication, l'Agent de fusion ou de distribution ne trouvera peut-être pas les fichiers d'instantanés dans le nouvel emplacement.  
  
> [!NOTE]  
>  Ne spécifiez pas un autre emplacement (à l’aide de la boîte de dialogue **Propriétés de la publication** ou [sp_changepublication &#40;Transact-SQL&#41;](../../relational-databases/system-stored-procedures/sp-changepublication-transact-sql.md)) qui soit identique à l’emplacement par défaut du dossier d’instantané.  
  
> [!CAUTION]  
>  N'utilisez pas WebSync et d'autres emplacements de dossier d'instantanés à la fois.  
  
#### <a name="use-sql-server-management-studio"></a>Utiliser SQL Server Management Studio
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
     Pour compresser les fichiers d'instantanés, sélectionnez **Compresser les fichiers d'instantanés à cet emplacement**. La compression est généralement utilisée avec les connexions à faible bande passante et d'autres emplacements d'instantané sur des supports amovibles, par exemple un CD-ROM.  
  
2.  Sélectionnez **OK**.  
  
#### <a name="use-transact-sql"></a>Utiliser Transact-SQL 

Lors de la [configuration des propriétés des instantanés &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md), définissez **snapshot_in_defaultfolder** avec la valeur false. 

## <a name="compressed-snapshots"></a>Instantanés compressés
  Vous pouvez choisir de compresser des fichiers d'instantanés lorsque vous transférez des instantanés sur un réseau lent ou lorsque vous les enregistrez sur un support amovible et que l'instantané non compressé est trop volumineux pour le support. Dans ces cas-là, la compression est utile mais il faut savoir qu'elle augmente le temps nécessaire à la génération et à l'application de l'instantané.  
  
 Les fichiers d'instantanés compressés sont enregistrés dans le format de fichier CAB de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , qui permet de compresser des fichiers de 2 Go au plus (si les fichiers d'instantanés ont une taille supérieure à 2 Go, leur compression est impossible). Pour compresser les fichiers, vous devez les écrire dans un autre dossier d'instantanés car les fichiers écrits dans le dossier d'instantanés par défaut ne peuvent pas être compressés. 
  
 Les fichiers sont décompressés à l'emplacement d'exécution de l'Agent de fusion ou de distribution ; les abonnements extraits sont généralement utilisés avec des instantanés compressés afin que les fichiers puissent être décompressés sur l'Abonné. Quand l'Abonné reçoit un fichier compressé, il l'enregistre tout d'abord dans un emplacement temporaire. Une fois le fichier compressé copié sur l'Abonné, les fichiers d'instantanés du fichier compressé sont décompressés dans l'ordre, fichier par fichier, par l'utilitaire CAB. L'espace nécessaire sur l'Abonné est égal à la taille du fichier compressé plus celle du fichier décompressé le plus volumineux.  
  
> [!NOTE]  
>  Compresser les instantanés permet dans certains cas d'améliorer les performances du transfert des fichiers d'instantanés sur le réseau. Toutefois, la compression de l'instantané nécessite un traitement supplémentaire de la part de l'Agent d'instantané lors de la génération des fichiers d'instantanés, et de la part de l'Agent de distribution lors de l'application de ces fichiers. Dans certains cas, cela peut ralentir la génération de l'instantané et rallonger le délai d'application d'un instantané. De plus, les instantanés compressés ne peuvent pas reprendre si une défaillance du réseau se produit ; ils ne conviennent donc pas aux réseaux non fiables. Évaluez ces différents facteurs avec précaution lors de l'utilisation d'instantanés compressés sur un réseau.  
  
### <a name="use-sql-server-management-studio"></a>Utiliser SQL Server Management Studio
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
        > [!NOTE]  
        >  Si cette case à cocher est activée, les fichiers stockés dans le dossier par défaut ne sont pas compressés. Les fichiers compressés peuvent être stockées uniquement à l'emplacement secondaire spécifié à l'étape précédente.  
  
2.  Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier**.    
3.  Sélectionnez **OK**.   

### <a name="use-transact-sql"></a>Utiliser Transact-SQL

Lors de la [configuration des propriétés des instantanés](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md), définissez **compress_snapshot** avec la valeur **True**. 

## <a name="execute-scripts-before-and-after-snapshot-is-applied"></a>Exécuter des scripts avant et après l’application d’un instantané
Vous pouvez spécifier les scripts à exécuter sur l'Abonné avant ou après l'application de l'instantané. Les scripts peuvent être utilisés à diverses fins, par exemple pour créer des connexions et des schémas (propriétaires d'objets) sur chaque Abonné.  
  
 Vous spécifiez un emplacement de fichier pour chaque script et l'Agent d'instantané copie les fichiers de script dans le dossier d'instantanés actif à chaque traitement d'instantané. L'Agent de distribution ou l'Agent de fusion exécute le script antérieur à l'instantané avant tout autre script d'objet répliqué lors de l'application d'un instantané. Il exécute le script postérieur à l'instantané après l'application de tous les autres scripts et données d'objets répliqués. Au terme de l'application de l'instantané et de l'exécution correcte des fichiers de script, ces derniers sont supprimés du répertoire de travail sur l'Abonné.  
  
 Le script est exécuté par le démarrage de l'utilitaire **sqlcmd** . Avant de déployer un script, exécutez-le avec **sqlcmd** pour vérifier qu'il s'exécute comme prévu. Le contenu des scripts exécutés avant et après l'application de l'instantané doit être renouvelable. Si, par exemple, vous créez une table dans le script, commencez par vérifier qu'elle existe et, dans l'affirmative, procédez de la façon appropriée. Le script doit être renouvelable car, s'il est nécessaire de réinitialiser un abonnement dont le script a déjà été appliqué, ce dernier sera réexécuté lors de l'application du nouvel instantané au cours de la réinitialisation.  
  
 Si vous compressez le fichier d'instantanés (en le convertissant au format de fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB), les scripts sont également compressés et placés dans le fichier CAB. Après le transfert du fichier d'instantanés compressé vers l'Abonné et sa décompression dans un répertoire de travail sur l'Abonné, tout script indiqué comme script antérieur à l'instantané est exécuté. De même, tous les scripts postérieurs à l'instantané sont décompressés et exécutés sur l'Abonné lors de l'étape finale de l'application de l'instantané.  

### <a name="execute-a-script"></a>Exécuter un script 

1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :    
    -   Pour spécifier un script à exécuter avant l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès pour le script dans la zone de texte **Exécuter ce script avant l'application de l'instantané** .  
  
        > [!NOTE]  
        >  Les Agents de distribution et de fusion doivent avoir des autorisations en lecture sur le répertoire spécifié. Si des abonnements par extraction sont utilisés, vous devez spécifier un répertoire partagé sous la forme d’un chemin UNC (Universal Naming Convention), par exemple \\\nom_ordinateur\scripts\mon_script.sql.  
  
    -   Pour spécifier un script à exécuter après l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès conforme à la convention d'affectation de noms (UNC) pour le script dans la zone de texte **Exécuter ce script après l'application de l'instantané** .   
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  


## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)   
 [Transférer un instantané par le biais du protocole FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md)   
 [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](../../relational-databases/replication/publish/configure-snapshot-properties-replication-transact-sql-programming.md)     
  
  
