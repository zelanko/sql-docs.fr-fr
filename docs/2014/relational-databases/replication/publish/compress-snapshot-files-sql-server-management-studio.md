---
title: Compresser des fichiers d’instantanés (SQL Server Management Studio) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
ms.assetid: 174ade3e-74a1-4e67-a6da-b874be3ff50f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 1451a8645edb5f1da2aa4590246b2e50ff73b4df
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48138159"
---
# <a name="compress-snapshot-files-sql-server-management-studio"></a>Compresser des fichiers d'instantanés (SQL Server Management Studio)
  Spécifiez que les fichiers doivent être compressés dans la page **Instantané** de la boîte de dialogue **Propriétés de publication - \<Publication>**. Pour plus d'informations sur l'accès à cette boîte de dialogue, consultez [Afficher et modifier les propriétés d’un serveur de publication](view-and-modify-publication-properties.md).  
  
### <a name="to-compress-snapshot-files"></a>Pour compresser des fichiers d'instantanés  
  
1.  Dans la page **Instantané** de la boîte de dialogue **Propriétés de la publication - \<Publication>**  :  
  
    1.  Sélectionnez **Placer les fichiers dans le dossier suivant**puis cliquez sur **Parcourir** pour accéder à un répertoire ou entrez le chemin d'accès au répertoire dans lequel stocker les fichiers d'instantanés.  
  
        > [!NOTE]  
        >  L'Agent d'instantané doit posséder des autorisations en écriture sur le répertoire spécifié et les Agents de distribution et de fusion des autorisations en lecture. Si vous utilisez des abonnements par extraction, vous devez définir un répertoire partagé en tant que chemin UNC, par exemple \\\nom_ordinateur\snapshot. Pour plus d’informations, consultez [Sécuriser le dossier d’instantanés](../security/secure-the-snapshot-folder.md).  
  
    2.  Désactivez la case à cocher **Placer les fichiers dans le dossier par défaut** sauf si les fichiers d'instantanés doivent être enregistrés dans les deux emplacements.  
  
        > [!NOTE]  
        >  Si cette case à cocher est activée, les fichiers stockés dans le dossier par défaut ne sont pas compressés. Les fichiers compressés peuvent être stockées uniquement à l'emplacement secondaire spécifié à l'étape précédente.  
  
2.  Sélectionnez **Compresser les fichiers d'instantanés dans ce dossier**.  
  
3.  [!INCLUDE[clickOK](../../../includes/clickok-md.md)]  
  
## <a name="see-also"></a>Voir aussi  
 [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](configure-snapshot-properties-replication-transact-sql-programming.md)   
 [Modifier les propriétés des publications et des articles](change-publication-and-article-properties.md)   
 [Instantanés compressés](../compressed-snapshots.md)   
 [Initialiser un abonnement avec un instantané](../initialize-a-subscription-with-a-snapshot.md)  
  
  
