---
title: "rsProcessingError - Erreur Reporting Services | Microsoft Docs"
ms.custom: ""
ms.date: "03/15/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "reporting-services-sharepoint"
  - "reporting-services-native"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "rsProcessingError"
ms.assetid: 414ee58a-8251-4367-9a8e-10c068d17280
caps.latest.revision: 29
author: "guyinacube"
ms.author: "asaxton"
manager: "erikre"
caps.handback.revision: 29
---
# rsProcessingError - Erreur Reporting Services
    
## Détails  
  
|||  
|-|-|  
|Nom du produit|[!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)]|  
|ID d'événement|rsProcessingError|  
|Source de l'événement|Microsoft.ReportingServices.Diagnostics.Utilities.ErrorStrings.resources|  
|Composant|[!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]|  
|Texte du message|Des erreurs se sont produites lors du traitement du rapport.|  
  
## Explication  
 Une ou plusieurs erreurs sont survenues pendant la publication, le traitement, l'aperçu local, l'affichage local depuis le serveur de rapports ou la création d'un abonnement pour un rapport. Ce message d'erreur indique qu'au moins une erreur a été détectée.  
  
### Causes possibles  
 Les causes possibles sont les suivantes :  
  
-   Une erreur de traitement s'est produite sur le serveur de rapports.  
  
-   Une erreur de traitement s'est produite pendant le traitement local d'un rapport lors de l'affichage de l'aperçu du rapport.  
  
-   Une expression de groupe a retourné un type de données incorrect.  
  
-   Une définition de filtre spécifiait deux expressions qui ont retourné des types de données qui n'ont pas pu être comparés.  
  
-   Une expression fait référence à un champ inexistant dans la collection de champs.  
  
-   Une expression contenait un appel de fonction d'agrégation dont l'étendue est non valide ou incompatible.  
  
-   Une expression fait référence à un paramètre inexistant dans la collection de paramètres du rapport.  
  
-   Un assembly personnalisé ou un assembly [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] qui a été incorrectement déployé n’a pas pu se charger.  
  
-   Un paramètre dont la propriété Nullable a la valeur **False** a détecté une valeur NULL dans le paramètre.  
  
-   Une expression pour la propriété Hidden d’une région de données contient une erreur : la référence d’objet n’est pas définie à une instance d’un objet.  
  
-   Une expression contenait un appel de fonction non valide ou une erreur de syntaxe.  
  
## Action de l'utilisateur  
  
### Sources d'informations complémentaires  
 Effectuez une ou plusieurs actions parmi les suivantes :  
  
-   Si vous affichez le rapport à partir du serveur de rapports ou si vous l'affichez en tant qu'abonnement, lisez l'intégralité du texte du message d'erreur. Le texte développé contient des informations supplémentaires.  
  
-   Si vous êtes en train de créer un rapport dans le Concepteur de rapports et que cette erreur s'affiche lors de l'aperçu ou de la publication du rapport, vous trouverez des informations supplémentaires dans la fenêtre Liste d'erreurs.  
  
-   Si vous êtes en train de créer un rapport dans l'Aperçu du Concepteur de rapports, lisez l'intégralité du texte du message d'erreur. Le texte développé contient des informations supplémentaires.  
  
-   Si vous affichez un rapport sur le serveur de rapports et que vous êtes connecté en tant qu’administrateur local sur le serveur de rapports, vous pouvez consulter la pile des appels en cliquant avec le bouton droit sur la page et en sélectionnant **Afficher la source**. La pile des appels contient des informations supplémentaires.  
  
-   Si vous êtes connecté en tant qu’administrateur local sur le serveur de rapports, recherchez `ReportProcessingException` dans le fichier journal. Les entrées du journal contiennent des informations supplémentaires. Le fichier journal du serveur de rapports se trouve généralement à l’emplacement suivant : \<*lecteur*>:\Program Files\Microsoft SQL Server\MSRS12.MSSQLSERVER\Reporting Services\LogFiles\ReportServerService__*horodatage*.log. Pour plus d’informations, consultez [Fichiers journaux et sources de Reporting Services](../../reporting-services/report-server/reporting-services-log-files-and-sources.md).  
  
### Échec du chargement de l'assembly hôte d'expressions  
 Les assemblys personnalisés doivent être signés par un nom fort et disposer de l’attribut AllowPartiallyTrustedCallers. Pour plus d’informations, consultez [Utilisation d’assemblys personnalisés avec des rapports](../../reporting-services/custom-assemblies/using-custom-assemblies-with-reports.md) et [Présentation des stratégies de sécurité](../../reporting-services/extensions/secure-development/understanding-security-policies.md).  
  
### Un nom global intégré n'existe pas  
 Vérifiez l'orthographe dans les expressions. Les noms de paramètres, de globales et de champs respectent la casse. Dans l'expression source de l'erreur, vérifiez que le nom existe réellement dans le rapport et qu'il est correctement orthographié. Pour plus d’informations, consultez [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md).  
  
### Propriétés de paramètre et valeur NULL  
 Un paramètre à valeurs multiples ne peut pas contenir la valeur NULL. Pour plus d’informations, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../../reporting-services/report-design/report-parameters-report-builder-and-report-designer.md).  
  
### Le rapport principal avec le sous-rapport n'a pas pu être traité  
 Un rapport avec des sous-rapports doit être traité par la même version du processeur de rapports [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)]. Lors de la mise à niveau de rapports vers la version actuelle du schéma de la définition de rapport, le rapport principal et les sous-rapports peuvent ou non ne pas être mis à jour en même temps. Si la version d'un rapport et de ses sous-rapports n'est pas compatible, le message suivant est affiché : « Le sous-rapport n'a pas pu être traité ».  
  
 Vous devez modifier le rapport principal ou les sous-rapports pour que tous les rapports puissent être traités par la même version du processeur de rapports. Pour plus d’informations sur la cause de l’échec de la mise à niveau d’un rapport, consultez [Mettre à niveau des rapports](../../reporting-services/install-windows/upgrade-reports.md).  
  
### Vérifier que les appels de fonction sont des appels de fonction Visual Basic et non SQL  
 Vous pouvez utiliser des fonctions SQL dans le texte des requêtes sur une base de données relationnelle. Vous ne pouvez pas utiliser de fonctions [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] dans le texte de requête.  
  
 Dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)], les expressions peuvent utiliser des fonctions [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)], des fonctions System.Math ou System.String, des fonctions [!INCLUDE[dnprdnshort](../../includes/dnprdnshort-md.md)] complètes ou des fonctions personnalisées que vous fournissez dans un code personnalisé ou dans un assembly personnalisé. Vous ne pouvez pas utiliser de fonctions SQL dans une expression.  
  
 Vérifiez que les appels de fonction effectués dans la requête et les expressions sont valides.  
  
### Impossible de comparer des types de données pour un filtre  
 Dans une équation de filtre, l'expression de filtre qui définit le contenu du filtre et la valeur du filtre doit être le même type de données pour être comparé. Si l'une des erreurs suivantes s'affichent, modifiez l'expression de champ ou la valeur de filtre pour que les types de données correspondent :  
  
-   Impossible d’effectuer le traitement de *\<type_élément_rapport>* pour l’élément *\<nom_élément_rapport>*. La comparaison des types de données *\<type>* et *\<type>* n’est pas possible. Vérifiez le type de données retourné par l’élément *\<nom_élément_rapport>*.  
  
-   Échec de l’évaluation de *\<nom_propriété>*.  
  
-   Échec de l’évaluation de *\<nom_propriété>*. Il fait référence à un champ de dataset qui contient une erreur : *\<chaîne_erreur>*.  
  
 Pour plus d’informations, consultez [Filtrer, regrouper et trier des données &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/filter-group-and-sort-data-report-builder-and-ssrs.md).  
  
### Spécification d'étendue non valide et incompatible dans un appel de fonction d'agrégation  
 Lorsque vous incluez des appels de fonction d'agrégation à une expression dans une cellule de tableau matriciel, le processeur de rapports évalue l'expression dans l'étendue des groupes intimes auxquels la cellule appartient.  
  
 Vous pouvez également passer le nom d'une étendue spécifique à une fonction d'agrégation. L'étendue peut faire référence au nom d'un dataset, une région de données ou le nom d'une étendue plus élevée dans la hiérarchie de données. Cela s'applique aux messages suivants :  
  
-   *\<type_élément_rapport>* ’*\<nom_élément_rapport>*’ a une étendue non valide « *\<nom_étendue>* ». L'étendue doit être l'étendue actuelle ou doit se trouver dans l'étendue actuelle.  
  
-   L’expression *\<nom_propriété>* pour l’élément *\<type_élément_rapport>* ’*\<nom_élément_rapport>*’ possède un paramètre d’étendue qui n’est pas valide pour une fonction d’agrégation. Le paramètre d'étendue doit être défini sur une constante de chaîne qui est égale au nom d'un groupe conteneur, au nom d'une région de données conteneur, ou au nom d'un dataset.  
  
 Pour les fonctions d’agrégation qui calculent des totaux cumulés (**Previous**, **RunningValue**, or **RowNumber**), vous pouvez spécifier un paramètre d’étendue qui est un nom de groupe de lignes ou un nom de groupe de colonnes, mais pas les deux. Cela s'applique au message d'erreur suivant :  
  
-   Les fonctions d’agrégation **Previous**, **RunningValue** ou **RowNumber** utilisées dans les cellules de données de *\<type_élément_rapport>* ’*\<nom_élément_rapport>*’ font référence à des étendues de regroupement dans des colonnes et des lignes de *\<type_élément_rapport>*. Les paramètres d’étendue de toutes les fonctions d’agrégation **Previous**, **RunningValue** et **RowNumber** de *\<type_élément_rapport>* peuvent faire référence à des regroupements de lignes ou à des regroupements de colonnes de données, mais pas aux deux.  
  
 Pour plus d’informations, consultez [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression scope for totals, aggregates, and built-in collections.md) et [Collections intégrées dans les expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/built-in-collections-in-expressions-report-builder-and-ssrs.md).  
  
### Étendue de dataset par défaut pour une zone de texte de niveau supérieur  
 N'utilisez pas d'étendue par défaut pour une zone de texte ajoutée à l'aire de conception du rapport lorsque le rapport a plusieurs dataset. Utilisez une expression qui inclut le nom du dataset comme étendue, et une fonction d'agrégation. Par exemple, `=First(Fields!FieldName.Value, "DataSet2")`.  
  
## Voir aussi  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expressions-report-builder-and-ssrs.md)   
 [Informations de référence sur les fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/aggregate-functions-reference-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/expression-examples-report-builder-and-ssrs.md)   
 [Jeux de données du rapport &#40;SSRS&#41;](../../reporting-services/report-data/report-datasets-ssrs.md)   
 [Filtres couramment utilisés &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/commonly-used-filters-report-builder-and-ssrs.md)   
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Code personnalisé et références d’assembly dans les expressions du Concepteur de rapports &#40;SSRS&#41;](../../reporting-services/report-design/custom-code-and-assembly-references-in-expressions-in-report-designer-ssrs.md)   
 [Informations de référence sur la collection de paramètres &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/parameters-collection-references-report-builder-and-ssrs.md)  
  
  