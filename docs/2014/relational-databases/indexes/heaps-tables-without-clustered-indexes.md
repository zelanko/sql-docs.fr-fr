---
title: Segments (tables sans index cluster) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: table-view-index
ms.topic: conceptual
helpviewer_keywords:
- heaps
ms.assetid: df5c4dfb-d372-4d0f-859a-a2d2533ee0d7
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: de71808c54264639aea82fe66cf23a7bfd6bd0ab
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63162150"
---
# <a name="heaps-tables-without-clustered-indexes"></a>Segments (tables sans index cluster)
  Un segment est une table sans index cluster. Un ou plusieurs index non cluster peuvent être créés sur des tables stockées comme segment. Les données sont stockées dans le segment sans spécifier d'ordre. Généralement, les données sont stockées initialement dans l'ordre dans lequel les lignes sont insérées dans la table, mais le [!INCLUDE[ssDE](../../includes/ssde-md.md)] peut déplacer des données dans le segment pour stocker les lignes efficacement ; l'ordre des données ne peut donc pas être prédit. Pour garantir l'ordre des lignes retournées à partir d'un segment, vous devez utiliser la clause `ORDER BY`. Pour spécifier l'ordre de stockage des lignes, créez un index cluster sur la table, de sorte que la table ne soit pas un segment.  
  
> [!NOTE]  
>  Il existe parfois de bonnes raisons de conserver une table comme segment plutôt que de créer un index cluster, mais l'utilisation de segments est effectivement une compétence avancée. La plupart des tables doivent avoir un index cluster soigneusement choisi, à moins qu'il n'existe une bonne raison de conserver la table comme segment.  
  
## <a name="when-to-use-a-heap"></a>À quel moment utiliser un segment  
 Si une table est un segment et ne possède pas d'index non cluster, la table entière doit être examinée (analyse de table) pour rechercher une ligne quelconque. Cela peut être acceptable lorsque la table est minuscule, par exemple s'il s'agit d'une liste des 12 bureaux régionaux d'une société.  
  
 Lorsqu'une table est stockée en tant que segment, les différentes lignes sont identifiées par référence à un identificateur de ligne (RID) composé d'un numéro de fichier, d'un numéro de page de données et de l'emplacement sur la page. L'ID de ligne est une structure petite et efficace. Parfois, les architectes de données utilisent des segments lorsque l'accès aux données s'effectue toujours par le biais d'index non cluster et que le RID est plus petit que la clé d'index cluster.  
  
## <a name="when-not-to-use-a-heap"></a>À quel moment ne pas utiliser un segment  
 N'utilisez pas de segment lorsque les données sont souvent retournées dans un ordre trié. Un index cluster sur la colonne de tri peut éviter l'opération de tri.  
  
 N'utilisez pas de segment lorsque les données sont souvent regroupées. Les données doivent être triées avant d'être regroupées et un index cluster sur la colonne de tri peut éviter l'opération de tri.  
  
 N'utilisez pas de segment lorsque des plages de données sont souvent interrogées pour la table.  Un index cluster sur la colonne de plages évitera de devoir trier le segment entier.  
  
 N'utilisez pas de segment lorsqu'il n'y a pas d'index non cluster et que la table est grande. Dans un segment, toutes les lignes du segment doivent être lues pour trouver n'importe une ligne quelconque.  
  
## <a name="managing-heaps"></a>Gestion des segments  
 Pour créer un segment, créez une table sans index cluster. Si la table possède déjà un index cluster, supprimez-le afin de reconvertir la table en segment.  
  
 Pour supprimer un segment, créez un index cluster sur le segment.  
  
 Pour reconstruire un segment afin de récupérer de l'espace perdu, créez un index cluster sur le segment, puis supprimez l'index cluster.  
  
> [!WARNING]  
>  La création ou suppression d'index cluster nécessite de réécrire la table entière. Si la table a des index non cluster, tous les index non cluster doivent être recréés à chaque fois que l'index cluster est modifié. Par conséquent, le passage d’un segment à une structure d’index cluster (ou inversement) peut prendre beaucoup de temps et nécessiter de l’espace disque pour réorganiser les données dans tempdb.  
  
## <a name="related-content"></a>Contenu associé  
 [CREATE INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-index-transact-sql)  
  
 [DROP INDEX &#40;Transact-SQL&#41;](/sql/t-sql/statements/drop-index-transact-sql)  
  
 [Description des index cluster et non-cluster](clustered-and-nonclustered-indexes-described.md)  
  
  
