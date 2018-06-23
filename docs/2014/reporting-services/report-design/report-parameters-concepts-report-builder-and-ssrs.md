---
title: État de Concept des paramètres (Générateur de rapports et SSRS) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b0aa2159-4e49-4713-8824-5ef9a9edbc62
caps.latest.revision: 8
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3df4f17a75018c3b78653f5b0fb9419d3835f9e5
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36152488"
---
# <a name="report-parameters-concept-report-builder-and-ssrs"></a>Concept des paramètres de rapport (Générateur de rapports et SSRS)
  Vous pouvez ajouter des paramètres à un rapport pour lier des rapports connexes, pour contrôler l'apparence d'un rapport, pour filtrer les données du rapport, ou pour limiter l'étendue d'un rapport à des utilisateurs ou des emplacements spécifiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
 Les paramètres de rapport sont créés des manières suivantes :  
  
-   Automatiquement, lorsque vous définissez la requête de dataset qui contient des variables de requête. Pour chaque variable de requête, un paramètre de requête de dataset et un paramètre de rapport correspondants portant les mêmes noms sont créés. Un paramètre de requête peut être une référence à une variable de requête ou à un paramètre d'entrée pour une procédure stockée.  
  
-   Automatiquement, lorsque vous ajoutez une référence à un dataset partagé qui contient des paramètres de requête.  
  
-   Manuellement, lorsque vous créez des paramètres de rapport dans le volet Données du rapport. Les paramètres font partie des collections intégrées que vous pouvez inclure dans une expression dans un rapport. Étant donné que les expressions sont utilisées pour définir des valeurs dans l'ensemble d'une définition de rapport, vous pouvez utiliser des paramètres pour contrôler l'apparence du rapport ou pour transmettre des valeurs aux sous-rapports ou aux rapports connexes qui utilisent également des paramètres.  
  
 Pour plus d’informations, consultez [Report Parameters &#40;Report Builder and Report Designer&#41;](report-parameters-report-builder-and-report-designer.md).  
  
 Les paramètres sont fréquemment utilisés pour filtrer des données de rapport à la fois avant et après le retour des données sur le rapport. Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](filter-group-and-sort-data-report-builder-and-ssrs.md)  
  
 Lorsque vous concevez un rapport, les paramètres de rapport sont enregistrés dans la définition de rapport. Lorsque vous publiez un rapport, les paramètres de rapport sont enregistrés et gérés indépendamment de la définition de rapport. Après avoir enregistré le rapport sur le serveur de rapports, vous pouvez effectuer les opérations suivantes :  
  
-   Modifiez des valeurs de paramètres du rapport directement sur le serveur de rapports, indépendamment de la définition de rapport.  
  
-   Créez plusieurs rapports liés dans lesquels chaque rapport lié est un lien vers la définition de rapport avec un jeu distinct de valeurs de paramètres pouvant être gérées indépendamment sur le serveur de rapports.  
  
 Si vous projetez de créer des instantanés de rapport, des historiques ou des abonnements à un rapport publié, vous devez comprendre l'effet des paramètres de rapport sur les exigences de conception du rapport.  
  
## <a name="see-also"></a>Voir aussi  
 [Concepts de création de rapports &#40;rapport Générateur et SSRS&#41;](report-authoring-concepts-report-builder-and-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](../report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Didacticiel : Ajouter un paramètre à votre rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)  
  
  