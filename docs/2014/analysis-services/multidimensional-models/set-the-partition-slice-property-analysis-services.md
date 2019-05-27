---
title: Définissez la propriété Slice de Partition (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 08/05/2015
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- partitions [Analysis Services], data slices
- data slices [Analysis Services]
ms.assetid: 507b91e5-7f85-4c22-be97-4d7a676e6667
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d9d7b41de3505c3b6e3ccf3886254958ee71e456
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66072942"
---
# <a name="set-the-partition-slice-property-analysis-services"></a>Définir la propriété Secteur de partition (Analysis Services)
  Une tranche de données est une fonctionnalité d'optimisation importante qui permet de diriger les requêtes vers les données des partitions appropriées. Définir explicitement la propriété Slice peut améliorer les performances des requêtes en remplaçant les tranches par défaut générées pour les partitions MOLAP ou HOLAP. En outre, la propriété Slice permet un contrôle de validation supplémentaire lors du traitement de la partition.  
  
 Vous pouvez spécifier une tranche de données après avoir créé une partition, mais avant son traitement, à l'aide de la propriété Slice. Sous l'onglet Partitions, développez un groupe de mesures, cliquez avec le bouton droit sur une partition, puis sélectionnez **Propriétés**.  
  
## <a name="defining-a-slice"></a>Définition d'une tranche  
 Les valeurs valides pour une propriété Slice sont les suivantes : un membre, un jeu ou un tuple MDX. Les exemples suivants illustrent la syntaxe valide de la propriété Slide :  
  
|Tranche|Membre, jeu ou tuple|  
|-----------|--------------------------|  
|[Date].[Calendar].[Calendar Year].&[2010]|Spécifiez cette tranche sur une partition contenant des faits de l'année 2010 (en partant du principe que le modèle inclut une dimension Date avec la hiérarchie Année civile, dont 2010 est un membre.) Bien que la table ou la clause WHERE de la source de partition soit peut-être déjà filtrée pour l'année 2010, spécifier la propriété Slice offre un contrôle supplémentaire au cours du traitement, ainsi que des analyses plus ciblées pendant l'exécution de la requête.|  
|{ [Sales Territory].[Sales Territory Country].&[Australia], [Sales Territory].[Sales Territory Country].&[Canada] }|Spécifiez cette tranche sur une partition contenant des faits qui incluent des informations sur le secteur de vente. Une tranche peut être un jeu MDX constitué de deux membres ou plus.|  
|[Measures].[Sales Amount Quota] > '5000'|Cette tranche représente une expression MDX.|  
  
 Une tranche de données d'une partition doit refléter, aussi fidèlement que possible, les données de la partition. Par exemple, si une partition est limitée aux données de l'année 2012, la tranche de données de la partition doit spécifier le membre 2012 de la dimension Time. Il n'est pas toujours possible de spécifier une tranche de données qui reflète le contenu exact d'une partition. Par exemple, si une partition contient des données uniquement pour janvier et février, alors que les niveaux de la dimension Time sont Year, Quarter et Month, l'Assistant Partition ne peut pas sélectionner à la fois les membres January et February. Dans de tels cas, sélectionnez le parent des membres qui reflètent le contenu de la partition. Dans cet exemple, sélectionnez Quarter 1.  
  
 Pour obtenir une explication des avantages que confère une tranche de données, consultez [Définir une tranche sur votre partition de cube SSAS](https://go.microsoft.com/fwlink/?LinkId=317783).  
  
> [!NOTE]  
>  Notez que les fonctions MDX dynamiques (telles que [Generate &#40;MDX&#41;](/sql/mdx/generate-mdx) ou [Except &#40;MDX&#41;](/sql/mdx/except-mdx-function)) ne sont pas prises en charge dans la propriété Slice des partitions. Vous devez définir la tranche à l'aide de tuples explicites ou de références à des membres.  
>   
>  Par exemple, au lieu d’utiliser le [: &#40;plage&#41; &#40;MDX&#41; ](/sql/mdx/range-mdx) de fonction pour définir une plage, vous devez énumérer chaque membre par année spécifique.  
>   
>  Si vous devez définir une tranche complexe, nous vous recommandons de définir les tuples de la tranche en utilisant un script XMLA Alter. Ensuite, vous pouvez utiliser l'outil en ligne de commande ascmd ou la [Analysis Services Execute DDL Task](../../integration-services/control-flow/analysis-services-execute-ddl-task.md) SSIS pour exécuter le script et créer le jeu de membres spécifié juste avant de traiter la partition.  
  
## <a name="see-also"></a>Voir aussi  
 [Créer et gérer une partition locale &#40;Analysis Services&#41;](create-and-manage-a-local-partition-analysis-services.md)  
  
  
