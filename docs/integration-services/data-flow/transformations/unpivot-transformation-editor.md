---
title: "&#201;diteur de transformation UnPivot | Microsoft Docs"
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
  - "sql13.dts.designer.unpivottransformation.f1"
helpviewer_keywords: 
  - "Éditeur de transformation UnPivot"
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
caps.latest.revision: 35
author: "douglaslMS"
ms.author: "douglasl"
manager: "jhubbard"
caps.handback.revision: 35
---
# &#201;diteur de transformation UnPivot
  Utilisez la boîte de dialogue **Éditeur de transformation UnPivot** pour sélectionner les colonnes à convertir en ligne, et définir la colonne de données et la nouvelle colonne de sortie de valeur croisée.  
  
> [!NOTE]  
>  Cette rubrique s’appuie sur le scénario Unpivot décrit dans [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md) pour illustrer l’utilisation des options.  
  
 Pour en savoir plus sur la transformation Unpivot, consultez [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md).  
  
## Options  
 **Colonnes d'entrée disponibles**  
 Définissez les colonnes à convertir en lignes en utilisant les cases à cocher.  
  
 **Nom**  
 Affiche le nom de la colonne d'entrée disponible.  
  
 **Transfert direct**  
 Indique s'il faut inclure la colonne dans la sortie supprimée du tableau croisé dynamique.  
  
 **Colonne d'entrée**  
 Sélectionnez dans la liste le nom d'une colonne d'entrée pour chaque ligne. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), les colonnes d'entrée sont **Ham**, **Soda**, **Milk**, **Beer**et **Chips** .  
  
 **Colonne de destination**  
 Définissez le nom de la colonne de données.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), la colonne de destination est la colonne de quantité (**Qty**).  
  
 **Valeur de clé de tableau croisé dynamique**  
 Tapez le nom de la valeur croisée dynamique. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), les valeurs croisées dynamiques apparaîtront dans la nouvelle colonne Produit définie par l'option **Nom de colonne de la valeur de clé de tableau croisé dynamique** comme les valeurs de texte **Ham**, **Soda**, **Milk**, **Beer**et **Chips**.  
  
 **Nom de colonne de la valeur de clé de tableau croisé dynamique**  
 Tapez le nom de la colonne de valeur croisée dynamique. La valeur par défaut est « Valeur de clé de tableau croisé dynamique ». Toutefois, vous pouvez choisir un nom descriptif unique.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](../../../integration-services/data-flow/transformations/unpivot-transformation.md), le nom de la colonne de la valeur de clé de tableau croisé dynamique est **Product** et définit la nouvelle colonne **Product** dans laquelle les colonnes **Ham**, **Soda**, **Milk**, **Beer**et **Chips** ne sont pas croisées dynamiquement.  
  
## Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../../integration-services/integration-services-error-and-message-reference.md)   
 [Transformation de tableau croisé dynamique](../../../integration-services/data-flow/transformations/pivot-transformation.md)  
  
  