---
title: "&#201;diteur de transformation de jointure de fusion | Microsoft Docs"
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
  - "sql13.dts.designer.mergejointransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de jointure de fusion"
ms.assetid: ac06f419-30b3-42aa-8b34-42000bec4285
caps.latest.revision: 31
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 31
---
# &#201;diteur de transformation de jointure de fusion
  La boîte de dialogue **Éditeur de transformation de jointure de fusion** permet de préciser le type de jointure, les colonnes qui composent cette dernière et les colonnes de sortie, afin de pouvoir fusionner deux entrées combinées par une opération de jointure.  
  
> [!IMPORTANT]  
>  La transformation de jointure de fusion requiert des données triées pour ses entrées. Pour plus d’informations sur cette spécification importante, consultez [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md).  
  
 Pour en savoir plus sur la transformation de jointure de fusion, consultez [Merge Join Transformation](../../../integration-services/data-flow/transformations/merge-join-transformation.md).  
  
## Options  
 **Type de jointure**  
 Permet de préciser l'utilisation d'une jointure interne, externe gauche ou entière.  
  
 **Échanger les entrées**  
 Permet d’intervertir l’ordre des entrées par le bouton **Échanger les entrées**. Ceci peut s'avérer utile dans le cas de jointure externe gauche.  
  
 **Entrée**  
 Permet de sélectionner, dans la liste des entrées disponibles, chaque colonne à inclure à la sortie fusionnée.  
  
 Les entrées se présentent sous forme de deux tables distinctes. Permet de choisir les colonnes à inclure dans la sortie. Pour créer une jointure entre tables, faites glisser les colonnes. Pour supprimer une jointure, sélectionnez-la et appuyez sur la touche Suppr.  
  
 **Colonne d'entrée**  
 Permet de choisir une colonne à inclure à la sortie fusionnée d'après la liste de colonnes disponibles dans l'entrée sélectionnée.  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Trier des données pour les transformations de fusion et de jointure de fusion](../../../integration-services/data-flow/transformations/sort-data-for-the-merge-and-merge-join-transformations.md)   
 [Étendre un dataset à l'aide de la transformation de jointure de fusion](../../../integration-services/data-flow/transformations/extend-a-dataset-by-using-the-merge-join-transformation.md)   
 [Transformation de fusion](../../../integration-services/data-flow/transformations/merge-transformation.md)   
 [Transformation d'union totale](../../../integration-services/data-flow/transformations/union-all-transformation.md)  
  
  