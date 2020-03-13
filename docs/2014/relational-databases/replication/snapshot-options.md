---
title: Modifier les options d’initialisation d’instantané pour la réplication SQL | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshot replication [SQL Server], options
- snapshots [SQL Server replication], options
ms.assetid: 759fab42-66c7-4541-a7a3-bb6fb868493c
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 2a611de458537156740521dae8b732eed3e2653c
ms.sourcegitcommit: 4baa8d3c13dd290068885aea914845ede58aa840
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79289477"
---
# <a name="modify-snapshot-initialization-options-for-sql-replication"></a>Modifier les options d’initialisation d’instantané pour la réplication SQL

Cet article explique comment modifier un certain nombre d’options lors de [l’initialisation d’un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md).

## <a name="snapshot-format"></a>Format d’instantané
  Spécifiez le format d’instantané dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](publish/view-and-modify-publication-properties.md).  

1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>** , sélectionnez **SQL Server natif - tous les Abonnés doivent être des serveurs qui exécutent SQL Server** ou **Caractère - obligatoire si un serveur de publication ou un Abonné n’exécute pas SQL Server**. 

    > [!NOTE]  
    >  Il est conseillé de sélectionner le format natif, à moins que cette publication ne doive prendre en charge les abonnements à une base de données [!INCLUDE[ssEW](../../../includes/ssew-md.md)] ou à une base de données non-[!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] .    
1.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="snapshot-folder-locations"></a>Emplacements des dossiers d’instantanés

### <a name="default-snapshot-location"></a>Emplacement par défaut des instantanés
Spécifiez l’emplacement par défaut des instantanés (SQL Server Management Studio) Spécifiez l’emplacement par défaut des instantanés dans la page **dossier d’instantanés** de l’Assistant Configuration de la distribution. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Configurer la publication et la distribution](configure-publishing-and-distribution.md). Si vous créez une publication sur un serveur qui n'est pas configuré en tant que serveur de distribution, spécifiez un emplacement d'instantanés par défaut dans la page **Dossier d'instantanés** de l'Assistant Nouvelle publication. Pour plus d’informations sur l’utilisation de cet Assistant, consultez [Créer une publication](publish/create-a-publication.md).  
  
 Modifiez l’emplacement par défaut des instantanés dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur de distribution>** . Pour plus d’informations, consultez [Afficher et modifier les propriétés d’un serveur de distribution ou d’un serveur de publication](view-and-modify-distributor-and-publisher-properties.md). Définissez le dossier d’instantanés pour chaque publication dans la boîte de dialogue **Propriétés de publication - \<Publication>** . Pour plus d'informations, voir [View and Modify Publication Properties](publish/view-and-modify-publication-properties.md).  
  
#### <a name="modify-the-default-snapshot-location"></a>Modifier l’emplacement par défaut des instantanés  
  
1.  Dans la page **Serveurs de publication** de la boîte de dialogue **Propriétés du serveur de distribution - \<Serveur_de_distribution>** , cliquez sur le bouton des propriétés ( **…** ) du serveur de publication pour lequel vous voulez modifier l’emplacement par défaut des captures instantanées.    
2.  Dans la boîte de dialogue **Propriétés du serveur de publication - \<Serveur de publication>** , entrez une valeur pour la propriété **Dossier des captures instantanées par défaut**.

    > [!NOTE]  
    >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md).    
1.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  

### <a name="alternate-snapshot-location"></a>Autre emplacement d’instantané
  Spécifiez un autre emplacement d’instantané dans la page **instantané** de la boîte de dialogue Propriétés de la publication ** \<->de publication** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](publish/view-and-modify-publication-properties.md). 

  
#### <a name="specify-an-alternate-snapshot-location"></a>Spécifier un autre emplacement d’instantané  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :    
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.    

        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md).    
    a.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.    
     Pour compresser les fichiers d'instantanés, sélectionnez **Compresser les fichiers d'instantanés à cet emplacement**. La compression est généralement utilisée avec les connexions à faible bande passante et d'autres emplacements d'instantané sur des supports amovibles, par exemple un CD-ROM.    
1.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]   


## <a name="compress-snapshot-files"></a>Compresser les fichiers d’instantanés
Spécifiez que les fichiers doivent être compressés dans la page **instantané** de la boîte de dialogue Propriétés de la publication ** \<->de publication** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](publish/view-and-modify-publication-properties.md).  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.    
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.    
        > [!NOTE]  
        >  Si cette case à cocher est activée, les fichiers stockés dans le dossier par défaut ne sont pas compressés. Les fichiers compressés peuvent être stockées uniquement à l'emplacement secondaire spécifié à l'étape précédente.    
2.  Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier**.    
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  

## <a name="execute-scripts-before-and-after-snapshot-is-applied"></a>Exécuter des scripts avant et après l’application d’un instantané

 Vous pouvez spécifier les scripts à exécuter sur l'Abonné avant ou après l'application de l'instantané. Les scripts peuvent être utilisés à diverses fins, par exemple pour créer des connexions et des schémas (propriétaires d'objets) sur chaque Abonné.  
  
 Vous spécifiez un emplacement de fichier pour chaque script et l'Agent d'instantané copie les fichiers de script dans le dossier d'instantanés actif à chaque traitement d'instantané. L'Agent de distribution ou l'Agent de fusion exécute le script antérieur à l'instantané avant tout autre script d'objet répliqué lors de l'application d'un instantané. Il exécute le script postérieur à l'instantané après l'application de tous les autres scripts et données d'objets répliqués. Au terme de l'application de l'instantané et de l'exécution correcte des fichiers de script, ces derniers sont supprimés du répertoire de travail sur l'Abonné.  
  
 Le script est exécuté par le démarrage de l'utilitaire **sqlcmd** . Avant de déployer un script, exécutez-le avec **sqlcmd** pour vérifier qu'il s'exécute comme prévu. Le contenu des scripts exécutés avant et après l'application de l'instantané doit être renouvelable. Si, par exemple, vous créez une table dans le script, commencez par vérifier qu'elle existe et, dans l'affirmative, procédez de la façon appropriée. Le script doit être renouvelable car, s'il est nécessaire de réinitialiser un abonnement dont le script a déjà été appliqué, ce dernier sera réexécuté lors de l'application du nouvel instantané au cours de la réinitialisation.  
  
 Si vous compressez le fichier d'instantanés (en le convertissant au format de fichier [!INCLUDE[msCoName](../../includes/msconame-md.md)] CAB), les scripts sont également compressés et placés dans le fichier CAB. Après le transfert du fichier d'instantanés compressé vers l'Abonné et sa décompression dans un répertoire de travail sur l'Abonné, tout script indiqué comme script antérieur à l'instantané est exécuté. De même, tous les scripts postérieurs à l'instantané sont décompressés et exécutés sur l'Abonné lors de l'étape finale de l'application de l'instantané.  

### <a name="execute-a-script-before-or-after-a-snapshot-is-applied"></a>Exécuter un script avant ou après l’application d’un instantané  
 Spécifiez un script facultatif à exécuter avant ou après l’application de l’instantané dans la page **instantané** de la boîte de dialogue Propriétés de la **publication \<->de publication** . Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](publish/view-and-modify-publication-properties.md).  


1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :    
    -   Pour spécifier un script à exécuter avant l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès pour le script dans la zone de texte **Exécuter ce script avant l'application de l'instantané** . 
   
        > [!NOTE]  
        >  Les Agents de distribution et de fusion doivent avoir des autorisations en lecture sur le répertoire spécifié. Si des abonnements par extraction sont utilisés, vous devez spécifier un répertoire partagé sous la forme d’un chemin UNC (Universal Naming Convention), par exemple \\\nom_ordinateur\scripts\mon_script.sql.    
    -   Pour spécifier un script à exécuter après l'application de l'instantané, cliquez sur **Parcourir** pour rechercher le script, ou entrez un chemin d'accès conforme à la convention d'affectation de noms (UNC) pour le script dans la zone de texte **Exécuter ce script après l'application de l'instantané** .    
2.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
  
  
