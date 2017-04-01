---
title: "&#201;diteur de transformation d&#39;&#233;chantillonnage de ligne (page &#201;chantillonnage) | Microsoft Docs"
ms.custom: ""
ms.date: "03/01/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "integration-services"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "sql13.DTS.DESIGNER.ROWSAMPLINGTRANSFORMATION.COLUMNS.F1"
  - "sql13.dts.designer.rowsamplingtransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation d'échantillonnage de ligne"
ms.assetid: 544c7709-6de0-4c08-bda3-759985be9a05
caps.latest.revision: 23
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 23
---
# &#201;diteur de transformation d&#39;&#233;chantillonnage de ligne (page &#201;chantillonnage)
  Utilisez la boîte de dialogue **Éditeur de transformation d'échantillonnage de ligne** pour échantillonner une partie d'une entrée à l'aide d'un nombre de lignes spécifié. Cette transformation divise l'entrée en deux sorties distinctes.  
  
 Pour en savoir plus sur la transformation d'échantillonnage de lignes, consultez [Row Sampling Transformation](../../../integration-services/data-flow/transformations/row-sampling-transformation.md).  
  
## Options  
 **Nombre de lignes**  
 Définissez le nombre de lignes de l'entrée à utiliser comme échantillon.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 **Nom de sortie de l'exemple**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes échantillonnées. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Nom de sortie non sélectionnée**  
 Fournissez un nom unique pour la sortie qui contiendra les lignes exclues de l'échantillonnage. Le nom fourni sera affiché dans le concepteur SSIS.  
  
 **Utiliser la valeur de départ aléatoire suivante**  
 Définissez la valeur de départ d'échantillonnage du générateur de nombres aléatoires qu'utilise la transformation pour créer un échantillon. Ceci est recommandé uniquement pour le développement et les tests. La transformation utilise le nombre de cycles Microsoft Windows comme valeur de départ si une valeur de départ aléatoire n'est pas définie.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Transformation de l'échantillonnage du pourcentage](../../../integration-services/data-flow/transformations/percentage-sampling-transformation.md)  
  
  