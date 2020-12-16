---
description: Segments (tables sans index cluster)
title: Segments (tables sans index cluster) | Microsoft Docs
ms.custom: ''
ms.date: 11/01/2016
ms.prod: sql
ms.prod_service: table-view-index, sql-database
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
- forward record
- forwarded record
- forwarding pointer
- RID
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
monikerRange: =azuresqldb-current||>=sql-server-2016||>=sql-server-linux-2017||=azuresqldb-mi-current
ms.openlocfilehash: be2a84e21cc55340d675041cdd353dab887531c2
ms.sourcegitcommit: 1a544cf4dd2720b124c3697d1e62ae7741db757c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2020
ms.locfileid: "97465290"
---
# <a name="heaps-tables-without-clustered-indexes"></a>Segments (tables sans index cluster)
[!INCLUDE [SQL Server Azure SQL Database](../../includes/applies-to-version/sql-asdb.md)]

  Un segment est une table sans index cluster. Un ou plusieurs index non cluster peuvent être créés sur des tables stockées comme segment. Les données sont stockées dans le segment sans spécifier d'ordre. Généralement, les données sont stockées initialement dans l'ordre dans lequel les lignes sont insérées dans la table, mais le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut déplacer des données dans le segment pour stocker les lignes efficacement ; l'ordre des données ne peut donc pas être prédit. Pour garantir l'ordre des lignes retournées à partir d'un segment, vous devez utiliser la clause `ORDER BY`. Pour spécifier l’ordre logique permanent à appliquer au stockage des lignes, créez un index cluster sur la table, de sorte que celle-ci ne soit pas un segment de mémoire.  
  
> [!NOTE]  
> Il existe parfois de bonnes raisons de conserver une table comme segment plutôt que de créer un index cluster, mais l'utilisation de segments est effectivement une compétence avancée. La plupart des tables doivent avoir un index cluster soigneusement choisi, à moins qu'il n'existe une bonne raison de conserver la table comme segment.  
  
## <a name="when-to-use-a-heap"></a>À quel moment utiliser un segment  
Lorsqu’une table est stockée en tant que segment de mémoire, les différentes lignes sont identifiées par référence à un identificateur de ligne (RID) de 8 octets composé d’un numéro de fichier, d’un numéro de page de données et de l’emplacement dans la page (FileID:PageID:SlotID). L’ID de ligne est une structure petite et efficace. 

Les segments de mémoire peuvent être utilisés en tant que tables de mise en lots pour des opérations d’insertion volumineuses et non ordonnées. Étant donné que les données sont insérées sans appliquer un ordre strict, l’opération d’insertion est généralement plus rapide que l’insertion équivalente dans un index cluster. Si les données du segment de mémoire sont lues et traitées dans une destination finale, il peut être utile de créer un index non cluster étroit qui couvre le prédicat de recherche utilisé par la requête de lecture. 

> [!NOTE]  
> Les données sont récupérées d’un segment de mémoire dans l’ordre des pages de données, mais pas nécessairement l’ordre dans lequel les données ont été insérées. 

Parfois, les professionnels des données utilisent des segments de mémoire lorsque l’accès aux données s’effectue toujours par le biais d’index non-cluster et que le RID est plus petit que la clé d’index cluster. 

Si une table est un segment de mémoire et si elle ne comprend pas d’index non-cluster, la table doit être lue dans son intégralité (analyse de table) pour trouver une ligne quelconque. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] ne peut pas rechercher un RID directement dans le segment de mémoire. Cela peut être acceptable si la table est petite.  
  
## <a name="when-not-to-use-a-heap"></a>À quel moment ne pas utiliser un segment  
 N'utilisez pas de segment lorsque les données sont souvent retournées dans un ordre trié. Un index cluster sur la colonne de tri peut éviter l'opération de tri.  
  
 N'utilisez pas de segment lorsque les données sont souvent regroupées. Les données doivent être triées avant d'être regroupées et un index cluster sur la colonne de tri peut éviter l'opération de tri.  
  
 N'utilisez pas de segment lorsque des plages de données sont souvent interrogées pour la table. Un index cluster sur la colonne de plages évitera de devoir trier le segment entier.  
  
 N’utilisez pas de segment de mémoire s’il n’y a pas d’index non-cluster et si la table est volumineuse, sauf si vous envisagez de retourner l’intégralité du contenu de la table, sans spécifier d’ordre. Dans un segment, toutes les lignes du segment doivent être lues pour trouver n'importe une ligne quelconque.  
 
 N’utilisez pas de segment de mémoire si les données sont fréquemment mises à jour. Si vous mettez à jour un enregistrement et que la mise à jour utilise plus d’espace dans les pages de données que celles-ci n’utilisent actuellement, l’enregistrement doit être déplacé vers une page de données qui dispose de suffisamment d’espace libre. Cela a pour effet de créer un **enregistrement transféré** pointant vers le nouvel emplacement des données. Le **pointeur de transfert** doit être écrit dans la page qui contenait ces données précédemment, afin d’indiquer le nouvel emplacement physique. Cela provoque la fragmentation du segment de mémoire. Lors de l’analyse d’un segment de mémoire, ces pointeurs doivent être suivis, ce qui limite les performances de lecture anticipée. En outre, cela peut entraîner des E/S supplémentaires, ce qui réduit les performances d’analyse. 
  
## <a name="managing-heaps"></a>Gestion des segments  
 Pour créer un segment, créez une table sans index cluster. Si la table possède déjà un index cluster, supprimez-le afin de reconvertir la table en segment.  
  
 Pour supprimer un segment, créez un index cluster sur le segment.  
  
 Pour reconstruire un segment afin de récupérer de l’espace perdu :
 -  Créez un index cluster dans le segment, puis supprimez cet index.  
 -  Utilisez la commande `ALTER TABLE ... REBUILD` pour reconstruire le segment de mémoire.
  
> [!WARNING]  
> La création ou suppression d'index cluster nécessite de réécrire la table entière. Si la table a des index non cluster, tous les index non cluster doivent être recréés à chaque fois que l'index cluster est modifié. Par conséquent, le passage d’un segment à une structure d’index cluster (ou inversement) peut prendre beaucoup de temps et nécessiter de l’espace disque pour réorganiser les données dans tempdb.  

## <a name="heap-structures"></a>Structures des segments
Un segment est une table sans index cluster. Les segments ont une ligne dans [sys.partitions](../../relational-databases/system-catalog-views/sys-partitions-transact-sql.md), avec `index_id = 0` pour chaque partition utilisée par le segment. Par défaut, un segment comporte une partition unique. Lorsqu'un segment comporte plusieurs partitions, chacune d'elles possède une structure de segment contenant les données la concernant. Par exemple, si un segment comporte quatre partitions, il y a quatre structures de segment, une dans chaque partition.

Selon les types de données du segment, chaque structure contient une ou plusieurs unités d'allocation pour stocker et gérer les données d'une partition spécifique. Chaque segment de mémoire a au minimum une unité d’allocation `IN_ROW_DATA` par partition. Le segment de mémoire a aussi une unité d’allocation `LOB_DATA` par partition s’il contient des colonnes LOB (Large Object). En outre, il a une unité d’allocation `ROW_OVERFLOW_DATA` par partition s’il contient des colonnes de longueur variable qui dépassent la limite de taille de ligne de 8 060 octets.

La colonne `first_iam_page` de la vue système `sys.system_internals_allocation_units` pointe vers la première page IAM de la chaîne de pages IAM gérant l’espace alloué au segment de mémoire dans une partition spécifique. [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] utilise les pages IAM pour se déplacer dans le segment de mémoire. Les pages de données et les lignes qu'elles contiennent ne sont ni classées dans un ordre spécifique, ni liées. La seule connexion logique entre les pages de données concerne les informations enregistrées dans les pages IAM.

> [!IMPORTANT]  
> La vue système `sys.system_internals_allocation_units` est exclusivement réservée à un usage interne de [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]. La compatibilité future n'est pas garantie.
 
Les analyses de table ou les lectures séquentielles d'un segment explorent les pages IAM pour rechercher les étendues contenant des pages pour le segment. Comme la page IAM représente les étendues dans le même ordre d'apparition que dans les fichiers de données, les analyses en série du segment s'effectuent uniformément de haut en bas de chaque fichier. L'utilisation des pages IAM pour la définition de la séquence d'analyse signifie également que les lignes du segment ne sont généralement pas retournées dans l'ordre de leur insertion.

L’illustration suivante montre comment [!INCLUDE[ssDEnoversion](../../includes/ssdenoversion-md.md)] utilise les pages IAM pour extraire des lignes de données dans un segment d’une partition unique. 

![iam_heap](../../relational-databases/indexes/media/iam-heap.gif)
  
## <a name="related-content"></a>Contenu associé  
[CREATE INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/create-index-transact-sql.md)     
[DROP INDEX &#40;Transact-SQL&#41;](../../t-sql/statements/drop-index-transact-sql.md)     
[Description des index cluster et non cluster](../../relational-databases/indexes/clustered-and-nonclustered-indexes-described.md)     
  
  
