---
title: Boîte de dialogue Propriétés du DataSet, champs (Générateur de rapports) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- "10021"
ms.assetid: 75c7e54a-3d20-4c9a-88da-ab36dce2ce42
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: a5c8e5f256ae762989d6112cb09f846febecc4dd
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59936527"
---
# <a name="dataset-properties-dialog-box-fields-report-builder"></a>Boîte de dialogue Propriétés du dataset, Champs (Générateur de rapports)
  Sélectionnez **Champs** dans la boîte de dialogue **Propriétés du dataset** pour modifier la collection de champs pour le dataset du rapport. La liste des champs est automatiquement remplie, mais vous pouvez utiliser **Champs** pour ajouter, modifier, et supprimer les champs de requête et les champs calculés.  
  
 Les champs calculés sont pris en charge uniquement sur les datasets incorporés. Pour plus d’informations, consultez [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-data/report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md).  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Ajoutez un nouveau champ de requête ou calculé au dataset.  
  
 **Supprimer**  
 Supprimez le champ sélectionné du dataset.  
  
 **Nom de champ**  
 Tapez le nom du champ. Ce champ doit être unique dans le dataset. Pour chaque champ existant dans le dataset, le nom est prérempli.  
  
 **Champ Source**  
 Entrez une valeur pour le champ.  
  
 Pour un champ calculé, la source du champ doit être le nom d'un champ existant récupéré par la requête de dataset ou une expression que vous créez. Par exemple, pour créer un champ qui représente 10 fois la valeur du champ de requête Sales, utilisez l'expression `=10 * Fields!Sales.Value`.  
  
 Pour un champ de requête, la source du champ doit être le nom d'un champ existant récupéré par la requête de dataset.  
  
 **Expression (fx)**  
 Ajoutez ou modifiez une expression pour le nouveau champ calculé. Ce bouton apparaît uniquement lorsque vous cliquez sur **Ajouter** et sélectionnez **Champ calculé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Créer un dataset partagé ou incorporé &#40;Générateur de rapports et SSRS&#41;](report-data/create-a-shared-dataset-or-embedded-dataset-report-builder-and-ssrs.md)   
 [Aide du Générateur de rapports pour les boîtes de dialogue, les volets et les Assistants](../../2014/reporting-services/report-builder-help-for-dialog-boxes-panes-and-wizards.md)   
 [Boîte de dialogue Propriétés de DataSet, Options &#40;Générateur de rapports&#41;](report-data/dataset-properties-dialog-box-options-report-builder.md)   
 [Boîte de dialogue de propriétés de DataSet, filtres &#40;Générateur de rapports&#41;](../../2014/reporting-services/dataset-properties-dialog-box-filters-report-builder.md)   
 [Boîte de dialogue Propriétés de DataSet, paramètres &#40;Générateur de rapports&#41;](../../2014/reporting-services/dataset-properties-dialog-box-parameters-report-builder.md)   
 [Boîte de dialogue Propriétés de DataSet, requête &#40;Générateur de rapports&#41;](report-data/dataset-properties-dialog-box-query-report-builder.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)   
 [Connexions de données, sources de données et chaînes de connexion dans le Générateur de rapports](../../2014/reporting-services/data-connections-data-sources-and-connection-strings-in-report-builder.md)  
  
  
