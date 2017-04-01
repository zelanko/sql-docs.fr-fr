---
title: "&#201;diteur de transformation de tri | Microsoft Docs"
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
  - "sql13.dts.designer.sorttransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation de tri"
ms.assetid: 8ae23970-49a9-4d6d-9f15-c7074783347c
caps.latest.revision: 25
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 25
---
# &#201;diteur de transformation de tri
  Utilisez la boîte de dialogue **Éditeur de transformation de tri** pour sélectionner les colonnes à trier, définir l'ordre de tri et indiquer si les doublons sont supprimés.  
  
 Pour en savoir plus sur la transformation de tri, consultez [Sort Transformation](../../../integration-services/data-flow/transformations/sort-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 Définissez les colonnes à trier en utilisant les cases à cocher.  
  
 **Nom**  
 Affiche le nom de chaque colonne d'entrée disponible.  
  
 **Relais**  
 Indique s'il faut inclure la colonne dans la sortie triée.  
  
 **Colonne d'entrée**  
 Sélectionnez dans la liste le nom d'une colonne d'entrée pour chaque ligne. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 **Alias de sortie**  
 Permet de saisir un alias pour chaque colonne de sortie. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 **Type de tri**  
 Indiquez si vous voulez effectuer un tri croissant ou décroissant.  
  
 **Ordre de tri**  
 Indiquez l'ordre de tri des colonnes. Vous devez le faire manuellement pour chaque colonne.  
  
 **Indicateurs de comparaison**  
 Pour plus d’informations sur les options de comparaison de chaînes, consultez [Comparaison des données chaînes](../../../integration-services/data-flow/comparing-string-data.md).  
  
 **Supprimer les lignes avec des valeurs de tri en double**  
 Indiquez si la transformation copie les lignes en double dans la sortie de transformation ou crée une seule entrée pour tous les doublons en fonction des options de comparaison de chaînes définies.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)  
  
  