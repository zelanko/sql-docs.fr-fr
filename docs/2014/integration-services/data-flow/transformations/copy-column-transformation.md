---
title: Copie de colonne, transformation | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copycolumntrans.f1
helpviewer_keywords:
- columns [Integration Services], copying
- copying columns
- Copy Column transformation
ms.assetid: 1c72a313-9026-46bc-a57f-c6b3f47346f8
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 6d6c78e6dd604d5b7062ccebfcd4170fdee27578
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48064259"
---
# <a name="copy-column-transformation"></a>copie de colonnes (transformation)
  La transformation de copie de colonne crée de nouvelles colonnes en copiant des colonnes d'entrée et en ajoutant les nouvelles colonnes à la sortie de la transformation. Ultérieurement dans le flux de données, différentes transformations peuvent être appliquées aux copies de colonne. Par exemple, vous pouvez utiliser la transformation de copie de colonne pour créer une copie d'une colonne, puis convertir les données copiées en caractères majuscules à l'aide de la transformation de la table des caractères, ou appliquer des agrégations à la nouvelle colonne à l'aide de la transformation d'agrégation.  
  
## <a name="configuration-of-the-copy-column-transformation"></a>Configuration de la transformation de copie de colonne  
 Vous configurez la transformation de copie de colonne en spécifiant les colonnes d'entrée à copier. Vous pouvez créer plusieurs copies d'une colonne ou générer des copies de plusieurs colonnes en une même opération.  
  
 Cette transformation a une entrée et une sortie. Elle ne prend pas en charge de sortie d'erreur.  
  
 Vous pouvez définir les propriétés par le biais du concepteur [!INCLUDE[ssIS](../../../includes/ssis-md.md)] ou par programme.  
  
 Pour plus d’informations sur les propriétés définissables dans la boîte de dialogue **Éditeur de transformation de copie de colonne** , consultez [Éditeur de transformation de copie de colonne](../../copy-column-transformation-editor.md).  
  
 La boîte de dialogue **Éditeur avancé** reflète les propriétés qui peuvent être définies par programmation. Pour plus d'informations sur les propriétés définissables dans la boîte de dialogue **Éditeur avancé** ou par programmation, cliquez sur l'une des rubriques suivantes :  
  
-   [Propriétés communes](../../common-properties.md)  
  
-   [Propriétés personnalisées des transformations](transformation-custom-properties.md)  
  
 Pour plus d’informations sur la façon de définir des propriétés, consultez [Définir les propriétés d’un composant de flux de données](../set-the-properties-of-a-data-flow-component.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Flux de données](../data-flow.md)   
 [Transformations Integration Services](integration-services-transformations.md)  
  
  
