---
title: "Définir des clés primaires logiques dans une vue de Source de données (Analysis Services) | Documents Microsoft"
ms.custom: 
ms.date: 03/01/2017
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: 
ms.component: 
ms.reviewer: 
ms.suite: pro-bi
ms.technology:
- analysis-services
- analysis-services/multidimensional-tabular
- analysis-services/data-mining
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- removing logical primary keys
- logical primary keys [SQL Server]
- deleting logical primary keys
- data source views [Analysis Services], logical primary keys
ms.assetid: 172bc267-c637-4caa-bf55-0ba198d30b1e
caps.latest.revision: "36"
author: Minewiskan
ms.author: owend
manager: kfile
ms.workload: Inactive
ms.openlocfilehash: 8d38773feb45ada119da338ccf022630b4a781b8
ms.sourcegitcommit: f1a6944f95dd015d3774a25c14a919421b09151b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/08/2017
---
# <a name="define-logical-primary-keys-in-a-data-source-view-analysis-services"></a>Définir des clés primaires logiques dans une vue de source de données (Analysis Services)
[!INCLUDE[ssas-appliesto-sqlas](../../includes/ssas-appliesto-sqlas.md)]L’Assistant vue de Source de données et le Concepteur de vue de Source de données définissent automatiquement une clé primaire pour une table qui est ajoutée à une vue de source de données en fonction de la table de base de données sous-jacente.  
  
 Occasionnellement, vous pouvez définir manuellement une clé primaire dans une vue de source de données. Par exemple, pour des raisons de performance ou de conception, les tables d'une source de données ne contiennent pas forcément de colonnes clés primaires définies de manière explicite. Les vues et les requêtes nommées peuvent également omettre la colonne clé primaire d'une table. Si une table, une vue ou une requête nommée ne contient pas de clé primaire physique définie, vous pouvez manuellement définir une clé primaire logique sur la table, la vue ou la requête nommée dans le Concepteur de vue de source de données.  
  
## <a name="set-a-logical-primary-key"></a>Définir une clé primaire logique  
 Des clés primaires sont nécessaires dans [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] pour identifier de façon unique les enregistrements d’une table, pour identifier les colonnes clés dans les tables de dimension et pour prendre en charge les relations entre les tables, les vues et les requêtes nommées. Ces relations servent à construire des requêtes pour récupérer des données et des métadonnées dans les sources de données sous-jacentes et à tirer parti des fonctionnalités avancées de Business Intelligence.  
  
 Toutes les colonnes peuvent être utilisées pour la clé primaire logique, y compris un calcul nommé. Lorsque vous créez une clé primaire logique, une contrainte unique est créée dans la vue de source de données et marquée comme contrainte de clé primaire. Si la table sélectionnée contient une autre clé primaire logique, celle-ci est supprimée.  
  
1.  Dans [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)], ouvrez le projet ou connectez-vous à la base de données qui contient la vue de source de données dans laquelle vous souhaitez définir une clé primaire logique.  
  
2.  Dans l’Explorateur de solutions, développez le dossier **Vues des sources de données** , puis double-cliquez sur la vue de source de données.  
  
     Pour rechercher une table ou une vue, vous pouvez utiliser l’option **Rechercher une table** en cliquant sur le menu **Vue de source de données**  ou en cliquant avec le bouton droit dans une zone ouverte du volet **Tables** ou **Diagramme** .  
  
3.  Dans le volet **Tables** ou **Diagramme** , cliquez avec le bouton droit sur la ou les colonnes que vous souhaitez utiliser pour définir une clé primaire logique, puis cliquez sur **Définir la clé primaire logique**.  
  
     L'option permettant de définir une clé primaire logique est disponible uniquement pour les tables qui ne possèdent pas de clé primaire.  
  
     Notez qu'après avoir définir la clé, une icône de clé identifie les colonnes clés primaires.  
  
## <a name="see-also"></a>Voir aussi  
 [Vues de sources de données dans les modèles multidimensionnels](../../analysis-services/multidimensional-models/data-source-views-in-multidimensional-models.md)   
 [Définir des calculs nommés dans une vue de source de données &#40;Analysis Services&#41;](../../analysis-services/multidimensional-models/define-named-calculations-in-a-data-source-view-analysis-services.md)  
  
  
