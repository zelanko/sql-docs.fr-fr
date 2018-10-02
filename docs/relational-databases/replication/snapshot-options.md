---
title: Options d’instantané | Microsoft Docs
ms.custom: ''
ms.date: 03/14/2017
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
manager: craigg
ms.openlocfilehash: ffcdf512b6bfce575690b78cdae76155066be994
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47853117"
---
# <a name="snapshot-options"></a>Options d'instantané
[!INCLUDE[appliesto-ss-xxxx-xxxx-xxx-md](../../includes/appliesto-ss-xxxx-xxxx-xxx-md.md)]
  Il existe de nombreuses options disponibles lors de l'initialisation d'un abonnement avec un instantané :  
  
-   Spécifier un emplacement de dossier d'instantanés de remplacement à la place ou en plus de l'emplacement de dossier d'instantanés par défaut. Pour plus d’informations, consultez [Alternate Snapshot Folder Locations](../../relational-databases/replication/alternate-snapshot-folder-locations.md).  
  
-   Compresser les instantanés pour un stockage sur support amovible ou pour un transfert sur un réseau lent. Pour plus d’informations, voir [Compressed Snapshots](../../relational-databases/replication/compressed-snapshots.md).  
  
-   Exécuter des scripts [!INCLUDE[tsql](../../includes/tsql-md.md)] avant ou après l'application de l'instantané. Pour plus d’informations, consultez [Exécuter des scripts avant et après l’application de l’instantané](../../relational-databases/replication/execute-scripts-before-and-after-the-snapshot-is-applied.md).  
  
-   Transférer des fichiers d'instantanés via le protocole FTP. Pour plus d’informations, consultez [Transférer des instantanés via FTP](../../relational-databases/replication/transfer-snapshots-through-ftp.md).  
  
## <a name="see-also"></a> Voir aussi  
 [Initialiser un abonnement avec un instantané](../../relational-databases/replication/initialize-a-subscription-with-a-snapshot.md)  
  
  
