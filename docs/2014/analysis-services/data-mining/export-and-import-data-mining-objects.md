---
title: Exporter et importer des objets d’exploration de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- backing up databases [Analysis Services]
- exporting mining models
- exporting mining structures
- mining structures [Analysis Services], creating
- mining structures [DMX], exporting
- mining models [Analysis Services], migration
ms.assetid: 10a83b13-2640-4ff5-80c8-a35e1d692908
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: c2f79f8bf9a1d0ff01ba97d29662fab026d4adcd
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66084469"
---
# <a name="export-and-import-data-mining-objects"></a>Exporter et importer des objets d'exploration de données
  Outre les fonctionnalités fournies dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour la sauvegarde, la restauration et la migration des solutions, l'exploration de données SQL Server permet de transférer rapidement des modèles et des structures d'exploration de données entre différents serveurs en utilisant des instructions DMX (Data Mining Extensions).  
  
 Si votre solution d'exploration de données utilise des données relationnelles au lieu d'une base de données multidimensionnelle, le transfert de modèles à l'aide des commandes `EXPORT` et `IMPORT` est beaucoup plus rapide et plus facile qu'en utilisant la restauration de base de données ou qu'en déployant une solution dans son intégralité.  
  
 Cette section présente la procédure de transfert des modèles et des structures d'exploration de données à l'aide d'instructions DMX. Pour obtenir des détails sur la syntaxe, ainsi que des exemples, consultez [EXPORT &#40;DMX&#41;](/sql/dmx/export-dmx) et [IMPORT &#40;DMX&#41;](/sql/dmx/import-dmx).  
  
> [!NOTE]  
>  Pour exporter ou importer les objets d'une base de données Microsoft SQL Server Analysis Services, vous devez être administrateur de base de données ou de serveur.  
  
## <a name="exporting-data-mining-structures"></a>Exportation de structures d'exploration de données  
 Lorsque vous exportez une structure d'exploration de données, l'instruction EXPORT exporte tous les modèles associés. Pour contrôler les objets exportés, vous devez spécifier chaque objet par son nom.  
  
 Si la structure d'exploration de données a été traitée et que les résultats ont été mis en cache (comportement par défaut), lorsque vous exportez la structure d'exploration de données, la définition contient un résumé des données sur lesquelles la structure est basée. Pour supprimer ce résumé, vous devez effacer le cache associé à la structure d'exploration de données en effectuant une opération `Process Clear Structure`. Pour plus d’informations, consultez [Traiter une structure d’exploration de données](process-a-mining-structure.md).  
  
### <a name="exporting-data-mining-models"></a>Exportation de modèles d'exploration de données  
 Le mot clé `WITH DEPENDENCIES` vous permet d'exporter la source de données et la définition de la vue de source de données avec le modèle d'exploration de données et sa structure.  
  
 Lorsque vous exportez un modèle d'exploration de données sans exporter ses dépendances, l'instruction EXPORT exporte la définition du modèle et sa structure, mais pas la définition des sources de données. Par conséquent, après avoir importé le modèle d'exploration de données, vous pourrez le parcourir immédiatement. Toutefois, si vous souhaitez le retraiter sur le serveur cible ou exécuter des requêtes sur les données sous-jacentes, vous devez créer une source de données correspondante sur le serveur de destination.  
  
## <a name="importing-data-mining-structures-and-models"></a>Importation de modèles et de structures d'exploration de données  
 Lorsque vous importez un objet d'exploration de données, il est importé vers le serveur et la base de données auxquels vous êtes connecté lorsque vous exécutez l'instruction IMPORT. Si le fichier d'importation comporte une base de données qui n'existe pas sur le serveur, la base de données est créée.  
  
 Vous pouvez également importer un modèle ou une structure d'exploration de données à l'aide de la commande `Restore`. Vos modèles ou structures seront restaurés dans la base de données qui porte le même nom que celle à partir de laquelle ils ont été exportés. Pour plus d’informations, consultez [Options de restauration](../multidimensional-models/restore-options.md).  
  
## <a name="remarks"></a>Notes  
 Vous ne pouvez pas importer de modèle ou de structure dans un serveur si un modèle ou une structure portant le même nom existe déjà sur celui-ci. Par ailleurs, vous ne pouvez pas exporter un objet d'exploration de données, puis modifier son nom dans le fichier d'exportation. Par conséquent, si vous anticipez des conflits d'attribution de noms, vous devez soit supprimer l'objet d'exploration de données sur le serveur cible, soit renommer l'objet d'exploration de données avant d'exporter la définition.  
  
## <a name="see-also"></a>Voir aussi  
 [Gestion des solutions et des objets d'exploration de données](management-of-data-mining-solutions-and-objects.md)  
  
  
