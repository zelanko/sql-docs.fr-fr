---
title: Spécifier un autre emplacement de dossier d’instantané (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], alternate folder locations
- snapshot replication [SQL Server], alternate folder locations
- alternate snapshot folders [SQL Server replication]
ms.assetid: 9293f0eb-5531-47ec-b6e2-0392823ce5cc
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: cae9676985ce2858d7eae1e2f6dc139ee6e4ed54
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48132949"
---
# <a name="specify-an-alternate-snapshot-folder-location-sql-server-management-studio"></a>Spécifier un autre emplacement de dossier d'instantané (SQL Server Management Studio)
  Spécifiez un autre emplacement d’instantané dans la page **Instantané** de la boîte de dialogue **Propriétés de publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
### <a name="to-specify-an-alternate-snapshot-location"></a>Pour spécifier un autre emplacement d'instantané  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez spécifier un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
     Pour compresser les fichiers d'instantanés, sélectionnez **Compresser les fichiers d'instantanés à cet emplacement**. La compression est généralement utilisée avec les connexions à faible bande passante et d'autres emplacements d'instantané sur des supports amovibles, par exemple un CD-ROM.  
  
2.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Autres emplacements du dossier d’instantanés](../alternate-snapshot-folder-locations.md)   
 [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Spécifier l’emplacement par défaut des instantanés &#40;SQL Server Management Studio&#41;](../specify-the-default-snapshot-location-sql-server-management-studio.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Initialiser un abonnement avec un instantané](../initialize-a-subscription-with-a-snapshot.md)  
  
  
