---
title: Le volet de données (Générateur de rapports) du rapport | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- "10435"
helpviewer_keywords:
- Report Data pane
ms.assetid: 1492aa39-aeb1-4509-ab97-b9edd0901b7e
caps.latest.revision: 11
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: cf8180224bd06e2f5e38316c992063621796d42b
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36144213"
---
# <a name="report-data-pane-report-builder"></a>Volet des données de rapport (Générateur de rapports)
  Utilisez le volet **Données du rapport** pour consulter les paramètres, sources de données, datasets, collections de champs et images définis dans votre rapport. Le volet des données de rapportpropose une vue hiérarchique des éléments qui représentent les données de votre rapport. Les nœuds du niveau supérieur représentent les champs prédéfinis, paramètres et images, ainsi que les références de sources de données. Développez chaque nœud pour en afficher les éléments de données. Par exemple, lorsque vous développez un nœud de source de données, les datasets définis pour cette source de données apparaissent. Lorsque vous développez un dataset, sa collection de champs apparaît. Faites glisser des éléments vers l'aire de conception de rapport ou vers le volet Regroupement pour lier les données aux éléments de rapport sélectionnés dans la page du rapport. Pour plus d’informations, consultez [Mode Création de rapport &#40;Générateur de rapports&#41;](report-builder/report-design-view-report-builder.md).  
  
## <a name="options"></a>Options  
 **Champs prédéfinis**  
 Représente des champs communément utilisés dans un rapport, tels que le nom du rapport ou le numéro de page. Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](report-design/built-in-collections-in-expressions-report-builder.md).  
  
 **Paramètres**  
 Représente la collection des paramètres de rapport, chacun pouvant correspondre à une valeur unique ou à plusieurs valeurs. Pour plus d’informations, consultez [Report Parameters &#40;Report Builder and Report Designer&#41;](report-design/report-parameters-report-builder-and-report-designer.md).  
  
 **Images**  
 Représente l'ensemble d'images utilisé dans le rapport. Pour plus d’informations, consultez [Images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md).  
  
 **Sources de données**  
 Représente une source de données incorporée ou une référence à une source de données partagée. Une source de données représente une source de données pour le rapport. Une source de données est le nœud parent de la collection de datasets qui l'utilise. Pour plus d’informations, consultez [ajouter des données à un rapport &#40;le Générateur de rapports et SSRS&#41; ](report-data/report-datasets-ssrs.md) et [des connexions de données, les Sources de données et les chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md).  
  
 **Jeux de données**  
 Représente les données extraites d'une source de données suite à l'exécution d'une commande, par exemple, une requête [!INCLUDE[tsql](../includes/tsql-md.md)] qui extrait des données d'une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Un dataset est le nœud parent de la collection de champs spécifiée par la requête et comprend également des champs calculés. Le Générateur de rapports prend en charge des concepteurs de requêtes qui vous aident dans la spécification des requêtes. Pour plus d’informations, consultez [ajouter des données à un rapport &#40;le Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Volet de regroupement &#40;Générateur de rapports&#41;](report-design/grouping-pane-report-builder.md)   
 [Recherche, affichage et gestion de rapports &#40;Générateur de rapports et SSRS&#41;](report-builder/finding-viewing-and-managing-reports-report-builder-and-ssrs.md)  
  
  