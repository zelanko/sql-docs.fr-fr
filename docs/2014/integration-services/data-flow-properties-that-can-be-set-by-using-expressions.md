---
title: Les propriétés qui peuvent être définies en utilisant des Expressions de flux de données | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- SQL Server Integration Services packages, property expressions
- Integration Services packages, property expressions
- packages [Integration Services], properties
- SSIS packages, property expressions
- property expressions [Integration Services]
ms.assetid: cd0e171a-08be-45d6-81dc-ed94f37698b8
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: fbb609a65c70cb44c8fda81feb75927060ed289b
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62829142"
---
# <a name="data-flow-properties-that-can-be-set-by-using-expressions"></a>Propriétés du flux de données pouvant être définies à l’aide d’expressions
  Les valeurs de certaines propriétés d'objets de flux de données peuvent être spécifiées à l'aide d'expressions de propriété disponibles sur le conteneur de tâche de flux de données.  
  
 Pour plus d’informations sur l’utilisation d’expressions de propriété, consultez [Expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md).  
  
 Vous pouvez utiliser des expressions de propriété pour personnaliser les configurations de chaque instance déployée d'un package. Vous pouvez également utiliser des expressions de propriété pour spécifier des contraintes d’exécution pour un package à l’aide de l’option **/set** avec l’utilitaire d’invite de commandes **dtexec** . Par exemple, vous pouvez limiter le nombre maximal de threads (`MaximumThreads`) utilisés par la transformation de tri ou l'utilisation `MaxMemoryUsage` des transformations de regroupement probable et de recherche floue. Si elles sont libres, ces transformations peuvent mettre en cache de grandes quantités de données en mémoire.  
  
 Pour spécifier une expression de propriété pour une des propriétés d’objets de flux de données répertoriées dans cette rubrique, affichez la fenêtre **Propriétés** pour la tâche de flux de données en la sélectionnant sur l’aire **Flux de contrôle** du concepteur ou en sélectionnant l’onglet **Flux de données** du concepteur sans sélectionner de composant ou de chemin individuel. Sélectionnez la propriété **Expressions** , puis cliquez sur les points de suspension (...) pour afficher la boîte de dialogue de **l’Éditeur d’expressions de la propriété** . Déroulez la liste **Propriété** pour sélectionner une propriété, puis entrez une expression dans la zone de texte **Expression** ou cliquez sur les points de suspension (...) pour afficher la boîte de dialogue **Générateur d’expressions** .  
  
 La liste **Propriété** affiche les propriétés disponibles uniquement pour les objets de flux de données que vous avez déjà placés sur l’aire **Flux de données** du concepteur. Par conséquent, vous ne pouvez pas utiliser la liste **Propriété** pour consulter toutes les propriétés possibles des objets de flux de données qui prennent en charge les expressions de propriété. Par exemple, si vous avez placé une source Ado.net sur l’aire du concepteur, le **propriété** liste contient une entrée pour le `[ADO NET Source].[SqlCommand]` propriété. La liste affiche également de nombreuses propriétés de la tâche de flux de données elle-même.  
  
## <a name="properties-of-data-flow-objects-that-support-property-expressions"></a>Propriétés des objets de flux de données qui prennent en charge les expressions de propriété  
 Les valeurs des propriétés de la liste suivante peuvent être spécifiées à l'aide d'expressions de propriété.  
  
### <a name="data-flow-sources"></a>Sources de flux de données  
  
|Objet de flux de données|Propriété|  
|----------------------|--------------|  
|Source ADO NET|Propriété TableOrViewName<br /><br /> Propriété SQLCommand|  
|Source XML|Propriété XMLData<br /><br /> Propriété XMLSchemaDefinition|  
  
### <a name="data-flow-transformations"></a>Transformations du flux de données  
 Pour plus d’informations sur ces propriétés personnalisées, consultez [Propriétés personnalisées des transformations](data-flow/transformations/transformation-custom-properties.md).  
  
|Objet de flux de données|Propriété|  
|----------------------|--------------|  
|transformation de fractionnement conditionnel|Propriété FriendlyExpression|  
|Transformation de colonnes dérivées|Propriété FriendlyExpression|  
|Transformation de regroupement approximatif|Propriété MaxMemoryUsage|  
|transformation de recherche floue|Propriété MaxMemoryUsage|  
|Transformation de recherche|Propriété SQLCommand<br /><br /> Propriété SqlCommandParam|  
|transformation de commande OLE DB|Propriété SQLCommand|  
|transformation de l'échantillonnage du pourcentage|Propriété SamplingValue|  
|transformation de tableau croisé dynamique|Propriété PivotKeyValue|  
|transformation d'échantillonnage de lignes|Propriété SamplingValue|  
|transformation de tri|Propriété MaximumThreads|  
|Transformation Unpivot|Propriété PivotKeyValue|  
  
### <a name="data-flow-destinations"></a>Destinations du flux de données  
  
|Objet de flux de données|Propriété|  
|----------------------|--------------|  
|Destination ADO NET|Propriété TableOrViewName<br /><br /> Propriété BatchSize<br /><br /> Propriété CommandTimeout|  
|Destination de fichier plat|Propriété Header|  
|Destination [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Compact|Propriété TableName|  
|Destination [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]|Propriété BulkInsertTableName<br /><br /> Propriété BulkInsertFirstRow<br /><br /> Propriété BulkInsertLastRow<br /><br /> Propriété BulkInsertOrder<br /><br /> Propriété Timeout|  
  
## <a name="related-tasks"></a>Tâches associées  
  
-   [Ajouter ou modifier une expression de propriété](expressions/add-or-change-a-property-expression.md)  
  
## <a name="related-content"></a>Contenu associé  
 Article technique, [SSIS Expression Cheat Sheet](https://pragmaticworks.com/Resources/Cheat-Sheets/SSIS-Expression-Cheat-Sheet), sur pragmaticworks.com  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions de propriété dans des packages](expressions/use-property-expressions-in-packages.md)   
 [Propriétés communes](../../2014/integration-services/common-properties.md)   
 [Propriétés personnalisées de transformation](data-flow/transformations/transformation-custom-properties.md)   
 [Propriétés du chemin](../../2014/integration-services/path-properties.md)  
  
  
