---
title: Transformation copie de colonnes | Documents Microsoft
ms.custom: 
ms.date: 03/01/2017
ms.prod: sql-server-2016
ms.reviewer: 
ms.suite: 
ms.technology:
- integration-services
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- sql13.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
caps.latest.revision: 37
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.translationtype: MT
ms.sourcegitcommit: f3481fcc2bb74eaf93182e6cc58f5a06666e10f4
ms.openlocfilehash: 3039b400b136b62840c40b463bb1d8f53a43251d
ms.contentlocale: fr-fr
ms.lasthandoff: 08/03/2017

---
# <a name="copy-column-transformation"></a>copie de colonnes (transformation)
  La transformation de copie de colonne crée de nouvelles colonnes en copiant des colonnes d'entrée et en ajoutant les nouvelles colonnes à la sortie de la transformation. Ultérieurement dans le flux de données, différentes transformations peuvent être appliquées aux copies de colonne. Par exemple, vous pouvez utiliser la transformation de copie de colonne pour créer une copie d'une colonne, puis convertir les données copiées en caractères majuscules à l'aide de la transformation de la table des caractères, ou appliquer des agrégations à la nouvelle colonne à l'aide de la transformation d'agrégation.  
  
## <a name="configuration-of-the-copy-column-transformation"></a>Configuration de la transformation de copie de colonne  
 Vous configurez la transformation de copie de colonne en spécifiant les colonnes d'entrée à copier. Vous pouvez créer plusieurs copies d'une colonne ou générer des copies de plusieurs colonnes en une même opération.  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de copie de colonne** , consultez [Éditeur de transformation de copie de colonne](../../../integration-services/data-flow/transformations/copy-column-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programme. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programme, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](http://msdn.microsoft.com/library/51973502-5cc6-4125-9fce-e60fa1b7b796)  
  
-   [Propriétés personnalisées des transformations](../../../integration-services/data-flow/transformations/transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../../../integration-services/data-flow/set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../../../integration-services/data-flow/data-flow.md)   
 [Transformations Integration Services](../../../integration-services/data-flow/transformations/integration-services-transformations.md)  
  
  
