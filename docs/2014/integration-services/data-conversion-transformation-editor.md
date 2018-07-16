---
title: Éditeur de Transformation de Conversion de données | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.dataconversiontransformation.f1
helpviewer_keywords:
- Data Conversion Transformation Editor
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 330ac6f9211afbc1dd3e89d9d4c7298a41026f31
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37225971"
---
# <a name="data-conversion-transformation-editor"></a>Éditeur de transformation de conversion de données
  Utilisez la boîte de dialogue **Éditeur de transformation de conversion de données** pour sélectionner les colonnes à convertir, sélectionner le type de données de conversion des colonnes et définir les attributs de conversion.  
  
> [!NOTE]  
>  Le `FastParse` propriété des colonnes de sortie de la transformation de Conversion de données n’est pas disponible dans le **éditeur de Transformation de Conversion de données**, mais peut être définie à l’aide de la **éditeur avancé**. Pour plus d'informations sur cette propriété, consultez la section Transformation de conversion de données dans [Transformation Custom Properties](data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de conversion de données, consultez [Data Conversion Transformation](data-flow/transformations/data-conversion-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 Sélectionnez les colonnes à convertir en activant les cases à cocher. Les sélections ajoutent des colonnes d'entrée à la table ci-dessous.  
  
 **Colonne d'entrée**  
 Sélectionnez les colonnes à convertir dans la liste des colonnes d'entrée disponibles. Vos sélections sont reflétées dans les sélections de cases à cocher ci-dessus.  
  
 **Alias de sortie**  
 Tapez un alias pour chaque nouvelle colonne. La valeur par défaut est `Copy of` suivie du nom de colonne d’entrée ; Toutefois, vous pouvez choisir n’importe quel nom unique et descriptif.  
  
 **Type de données**  
 Sélectionnez un type de données dans la liste. Pour plus d’informations, consultez [Types de données Integration Services](data-flow/integration-services-data-types.md).  
  
 **Longueur**  
 Définissez la longueur de colonne pour les données de chaînes.  
  
 **Précision**  
 Définissez la précision des données numériques.  
  
 **Échelle**  
 Définissez l'échelle des données numériques.  
  
 **Page de codes**  
 Sélectionnez la page de codes appropriée pour les colonnes de type DT_STR.  
  
 **Configurer l'affichage des erreurs**  
 Indiquez la façon dont les erreurs au niveau des lignes sont gérées via la boîte de dialogue [Configurer la sortie d’erreur](../../2014/integration-services/configure-error-output.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Convertir des données en un type différent à l'aide de la transformation de conversion de données](data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  
