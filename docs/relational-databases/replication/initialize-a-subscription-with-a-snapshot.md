---
title: Initialiser un abonnement avec un instantané | Microsoft Docs
ms.custom: ''
ms.date: 03/01/2017
ms.prod: sql
ms.prod_service: database-engine
ms.reviewer: ''
ms.technology: replication
ms.topic: conceptual
helpviewer_keywords:
- snapshots [SQL Server replication], initializing subscriptions
- initializing subscriptions [SQL Server replication], snapshots
ms.assetid: 77a9ade2-cdc0-4ae9-a02d-6e29d7c2ada0
author: MashaMSFT
ms.author: mathoma
monikerRange: =azuresqldb-mi-current||>=sql-server-2016||=sqlallproducts-allversions
ms.openlocfilehash: 3624d1eef64f10ae93802c4a7514fd54edcc0e74
ms.sourcegitcommit: b2e81cb349eecacee91cd3766410ffb3677ad7e2
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/01/2020
ms.locfileid: "76287926"
---
# <a name="initialize-a-subscription-with-a-snapshot"></a>Initialiser un abonnement avec un instantané
[!INCLUDE[appliesto-ss-asdbmi-xxxx-xxx-md](../../includes/appliesto-ss-asdbmi-xxxx-xxx-md.md)]
  Lorsqu'une publication est créée, un instantané initial est généralement créé puis copié dans le dossier d'instantanés (cela se produit par défaut pour les publications de fusion créées avec l'Assistant Nouvelle publication). Il est ensuite appliqué à l'Abonné par l'Agent de distribution (pour les publications transactionnelles et d'instantané) ou l'Agent de fusion (pour les publications de fusion) lors de la synchronisation initiale de l'abonnement. Le processus d'instantané dépend du type de publication :  
  
-   Si l'instantané est pour une publication d'instantané, une publication transactionnelle ou une publication de fusion n'utilisant pas de filtres paramétrés, l'instantané contient le schéma et les données dans des fichiers programme (bcp) de copie en bloc, ainsi que des contraintes, des propriétés étendues, des index, des déclencheurs et les tables système nécessaires à la réplication. Pour plus d’informations sur la création et l’application de l’instantané, consultez [Créer et appliquer un instantané](../../relational-databases/replication/create-and-apply-the-initial-snapshot.md).  
  
-   Si l'instantané est pour une publication de fusion utilisant des filtres paramétrés, il est créé à l'aide d'un processus en deux parties. D'abord, un instantané de schéma est créé contenant les scripts de réplication et le schéma des objets publiés, mais pas les données. Ensuite, chaque abonnement est initialisé avec un instantané comprenant les scripts et le schéma copiés à partir de l'instantané de schéma et des données appartenant à la partition de l'abonnement. Pour plus d'informations, voir [Snapshots for Merge Publications with Parameterized Filters](../../relational-databases/replication/create-a-snapshot-for-a-merge-publication-with-parameterized-filters.md).  
  
 L'instantané se compose de fichiers différents qui dépendent du type de réplication et des articles que comprend la publication. Ces fichiers sont copiés sur le dossier d'instantanés par défaut spécifié lors de la configuration du serveur de distribution, ou sur le dossier d'instantanés de remplacement spécifié lors de la création de la publication.  
  
|Type de réplication|Fichiers d'instantanés courants|  
|-------------------------|---------------------------|  
|Réplication d'instantané ou réplication transactionnelle|schéma (.sch) ; données (.bcp) ; contraintes et index (.dri) ; contraintes (.idx) ; déclencheurs (.trg) : pour la mise à jour d'abonnés uniquement ; fichiers d'instantanés compressés (.cab).|  
|Réplication de fusion|schéma (.sch) ; données (.bcp) ; contraintes et index (.dri) ; déclencheurs (.trg) ; données des tables système (.sys) ; tables de conflits (.cft) ; fichiers d'instantanés compressés (.cab).|  
  
 Si le transfert de l'instantané est interrompu à n'importe quel moment, il reprendra automatiquement et ne renverra aucun fichier déjà transféré en totalité. L'unité de remise pour l'Agent d'instantané est le fichier bcp pour chaque article de publication, les fichiers partiellement remis doivent donc être remis à nouveau en totalité. Cependant, la reprise de l'instantané peut diminuer de manière significative la quantité de données transmise et garantir la remise de l'instantané en temps voulu, même si la connexion n'est pas fiable.  
  
## <a name="snapshot-options"></a>Options d'instantané  
 Il existe de nombreuses options disponibles lors de l'initialisation d'un abonnement avec un instantané. Vous pouvez :  
  
-   Spécifier un emplacement de dossier d'instantanés de remplacement à la place, ou en plus de l'emplacement de dossier d'instantanés par défaut. Pour plus d’informations, consultez [Modifier les options des instantanés](../../relational-databases/replication/snapshot-options.md).  
  
-   Compresser les instantanés pour un stockage sur support amovible ou pour un transfert sur un réseau lent. Pour plus d’informations, consultez [Compressed Snapshots](../../relational-databases/replication/snapshot-options.md#compressed-snapshots). 

-   Exécuter des scripts Transact-SQL avant ou après l'application de l'instantané. Pour plus d’informations, consultez [Exécuter des scripts avant et après l’application de l’instantané](../../relational-databases/replication/snapshot-options.md#execute-scripts-before-and-after-snapshot-is-applied).  
  
-   Transférer des fichiers d'instantanés via le protocole FTP. Pour plus d’informations, consultez [Transférer des instantanés via FTP](../../relational-databases/replication/publish/deliver-a-snapshot-through-ftp.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Initialiser un abonnement](../../relational-databases/replication/initialize-a-subscription.md)   
 [Sécuriser le dossier d’instantanés](../../relational-databases/replication/security/secure-the-snapshot-folder.md)  
  
  
