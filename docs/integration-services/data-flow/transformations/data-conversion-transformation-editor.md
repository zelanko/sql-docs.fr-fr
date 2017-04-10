---
title: "&#201;diteur de transformation de conversion de donn&#233;es | Microsoft Docs"
ms.custom: ""
ms.date: "03/07/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.dts.designer.dataconversiontransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de conversion de données"
ms.assetid: 7b4e4873-e8fe-4549-a965-65bebdb270bc
caps.latest.revision: 28
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 28
---
# &#201;diteur de transformation de conversion de donn&#233;es
  Utilisez la boîte de dialogue **Éditeur de transformation de conversion de données** pour sélectionner les colonnes à convertir, sélectionner le type de données de conversion des colonnes et définir les attributs de conversion.  
  
> [!NOTE]  
>  La propriété **FastParse** des colonnes de sortie de la transformation de conversion de données n'est pas disponible dans l' **Éditeur de transformation de conversion de données**, mais elle peut être définie à l'aide de l' **Éditeur avancé**. Pour plus d'informations sur cette propriété, consultez la section Transformation de conversion de données dans [Transformation Custom Properties](../../../integration-services/data-flow/transformations/transformation-custom-properties.md).  
  
 Pour en savoir plus sur la transformation de conversion de données, consultez [Data Conversion Transformation](../../../integration-services/data-flow/transformations/data-conversion-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 Sélectionnez les colonnes à convertir en activant les cases à cocher. Les sélections ajoutent des colonnes d'entrée à la table ci-dessous.  
  
 **Colonne d'entrée**  
 Sélectionnez les colonnes à convertir dans la liste des colonnes d'entrée disponibles. Vos sélections sont reflétées dans les sélections de cases à cocher ci-dessus.  
  
 **Alias de sortie**  
 Tapez un alias pour chaque nouvelle colonne. La valeur par défaut est **Copie de** suivi du nom de la colonne d'entrée. Toutefois, vous pouvez choisir n'importe quel nom descriptif unique.  
  
 **Type de données**  
 Sélectionnez un type de données dans la liste. Pour plus d’informations, consultez [Integration Services Data Types](../../../integration-services/data-flow/integration-services-data-types.md).  
  
 **Longueur**  
 Définissez la longueur de colonne pour les données de chaînes.  
  
 **Précision**  
 Définissez la précision des données numériques.  
  
 **Échelle**  
 Définissez l'échelle des données numériques.  
  
 **Page de codes**  
 Sélectionnez la page de codes appropriée pour les colonnes de type DT_STR.  
  
 **Configurer l'affichage des erreurs**  
 Indiquez la façon dont les erreurs au niveau des lignes sont gérées via la boîte de dialogue [Configurer la sortie d’erreur](../Topic/Configure%20Error%20Output.md).  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Convertir des données en un type différent à l'aide de la transformation de conversion de données](../../../integration-services/data-flow/transformations/convert-data-type-by-using-data-conversion-transformation.md)  
  
  