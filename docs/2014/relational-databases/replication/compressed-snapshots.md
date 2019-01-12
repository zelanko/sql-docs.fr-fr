---
title: Instantanés compressés | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], compressed
- snapshot replication [SQL Server], compressed snapshots
- compressed snapshots [SQL Server replication]
ms.assetid: 979ffa7c-3a88-4e70-8cf2-b8d452fd7a7f
author: MashaMSFT
ms.author: mathoma
manager: craigg
ms.openlocfilehash: 873a16f8e6dcc73b4f2b3da5727d49207252ca63
ms.sourcegitcommit: 7aa6beaaf64daf01b0e98e6c63cc22906a77ed04
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/09/2019
ms.locfileid: "54124279"
---
# <a name="compressed-snapshots"></a>Instantanés compressés
  Vous pouvez choisir de compresser des fichiers d'instantanés lorsque vous transférez des instantanés sur un réseau lent ou lorsque vous les enregistrez sur un support amovible et que l'instantané non compressé est trop volumineux pour le support. Dans ces cas-là, la compression est utile mais il faut savoir qu'elle augmente le temps nécessaire à la génération et à l'application de l'instantané.  
  
 Les fichiers d'instantanés compressés sont enregistrés dans le format de fichier CAB de [!INCLUDE[msCoName](../../includes/msconame-md.md)] , qui permet de compresser des fichiers de 2 Go au plus (si les fichiers d'instantanés ont une taille supérieure à 2 Go, leur compression est impossible). Pour compresser les fichiers, vous devez les écrire dans un autre dossier d'instantanés car les fichiers écrits dans le dossier d'instantanés par défaut ne peuvent pas être compressés. Pour plus d’informations sur les autres dossiers d’instantanés, consultez [Autres emplacements du dossier d’instantanés](alternate-snapshot-folder-locations.md).  
  
 Les fichiers sont décompressés à l'emplacement d'exécution de l'Agent de fusion ou de distribution ; les abonnements extraits sont généralement utilisés avec des instantanés compressés afin que les fichiers puissent être décompressés sur l'Abonné. Quand l'Abonné reçoit un fichier compressé, il l'enregistre tout d'abord dans un emplacement temporaire. Une fois le fichier compressé copié sur l'Abonné, les fichiers d'instantanés du fichier compressé sont décompressés dans l'ordre, fichier par fichier, par l'utilitaire CAB. L'espace nécessaire sur l'Abonné est égal à la taille du fichier compressé plus celle du fichier décompressé le plus volumineux.  
  
> [!NOTE]  
>  Compresser les instantanés permet dans certains cas d'améliorer les performances du transfert des fichiers d'instantanés sur le réseau. Toutefois, la compression de l'instantané nécessite un traitement supplémentaire de la part de l'Agent d'instantané lors de la génération des fichiers d'instantanés, et de la part de l'Agent de distribution lors de l'application de ces fichiers. Dans certains cas, cela peut ralentir la génération de l'instantané et rallonger le délai d'application d'un instantané. De plus, les instantanés compressés ne peuvent pas reprendre si une défaillance du réseau se produit ; ils ne conviennent donc pas aux réseaux non fiables. Évaluez ces différents facteurs avec précaution lors de l'utilisation d'instantanés compressés sur un réseau.  
  
 **Pour compresser et remettre des fichiers d'instantanés**  
  
-   [!INCLUDE[msCoName](../../includes/msconame-md.md)] [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)]: [Compresser des fichiers d’instantanés &#40;SQL Server Management Studio&#41;](snapshot-options.md#compress-snapshot-files)  
  
-   Programmation de la réplication [!INCLUDE[tsql](../../includes/tsql-md.md)] : [Configurer les propriétés d’instantané &#40;programmation Transact-SQL de la réplication&#41;](publish/configure-snapshot-properties-replication-transact-sql-programming.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement avec un instantané](initialize-a-subscription-with-a-snapshot.md)   
 [Options d’instantané](snapshot-options.md)  
  
  
