---
title: Boîte de dialogue Propriétés de DataSet, champs | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
f1_keywords:
- sql12.rtp.rptdesigner.datasetproperties.fields.f1
- "10140"
ms.assetid: e1367556-736e-4a6b-b9e7-10432a3e50b5
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3b1c49beb22a3a91e3d42aa7ce4ed99b5e107b4d
ms.sourcegitcommit: 8d6fb6bbe3491925909b83103c409effa006df88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/22/2019
ms.locfileid: "59956925"
---
# <a name="dataset-properties-dialog-box-fields"></a>Boîte de dialogue Propriétés du dataset, Champs
  Sélectionnez **Champs** dans la boîte de dialogue **Propriétés du dataset** pour modifier la collection de champs pour le dataset du rapport. La liste des champs est automatiquement remplie, mais vous pouvez utiliser **Champs** pour ajouter, modifier, et supprimer les champs de requête et les champs calculés.  
  
## <a name="options"></a>Options  
 **Ajouter**  
 Ajoutez un nouveau champ de requête ou un champ calculé au dataset.  
  
 **Supprimer**  
 Supprimez le champ sélectionné du dataset.  
  
 **Nom de champ**  
 Tapez le nom du champ. Ce champ doit être unique dans le dataset. Pour chaque champ existant dans la requête de dataset, le nom est pré-rempli.  
  
 **Champ Source**  
 Entrez une valeur pour le champ.  
  
 Pour un champ calculé, la source du champ doit être le nom d'un champ existant récupéré par la requête de dataset ou une expression que vous créez. Par exemple, pour créer un champ qui représente 10 fois la valeur du champ de requête Sales, utilisez l'expression `=10 * Fields!Sales.Value`.  
  
 Pour un champ de requête, la source du champ doit être le nom d'un champ existant récupéré par la requête de dataset.  
  
 **Expression (fx)**  
 Ajoutez ou modifiez une expression pour le champ calculé. Ce bouton apparaît uniquement lorsque vous cliquez sur **Ajouter** et sélectionnez **Champ calculé**.  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](report-data/dataset-fields-collection-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-data/report-datasets-ssrs.md)   
 [Expressions &#40;Générateur de rapports et SSRS&#41;](report-design/expressions-report-builder-and-ssrs.md)  
  
  
