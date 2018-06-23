---
title: Éditeur de Transformation UNPIVOT | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.dts.designer.unpivottransformation.f1
helpviewer_keywords:
- Unpivot Transformation Editor
ms.assetid: 72a36ef0-4070-4f6c-9c74-0720109617dd
caps.latest.revision: 34
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: 4d5cd47f0ab4aa9a1c3d2468ddd809846cb7b4c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042543"
---
# <a name="unpivot-transformation-editor"></a>Éditeur de transformation UnPivot
  Utilisez la boîte de dialogue **Éditeur de transformation UnPivot** pour sélectionner les colonnes à convertir en ligne, et définir la colonne de données et la nouvelle colonne de sortie de valeur croisée.  
  
> [!NOTE]  
>  Cette rubrique s’appuie sur le scénario Unpivot décrit dans [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md) pour illustrer l’utilisation des options.  
  
 Pour en savoir plus sur la transformation Unpivot, consultez [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md).  
  
## <a name="options"></a>Options  
 **Colonnes d'entrée disponibles**  
 Définissez les colonnes à convertir en lignes en utilisant les cases à cocher.  
  
 **Nom**  
 Affiche le nom de la colonne d'entrée disponible.  
  
 **Transfert direct**  
 Indique s'il faut inclure la colonne dans la sortie supprimée du tableau croisé dynamique.  
  
 **Colonne d'entrée**  
 Sélectionnez dans la liste le nom d'une colonne d'entrée pour chaque ligne. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), les colonnes d'entrée sont **Ham**, **Soda**, **Milk**, **Beer**et **Chips** .  
  
 **Colonne de destination**  
 Définissez le nom de la colonne de données.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), la colonne de destination est la colonne de quantité (**Qty**).  
  
 **Valeur de clé de tableau croisé dynamique**  
 Tapez le nom de la valeur croisée dynamique. Par défaut, il s'agit du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
 Il est possible de spécifier la valeur de cette propriété en utilisant l'expression d'une propriété.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), les valeurs croisées dynamiques apparaîtront dans la nouvelle colonne Produit définie par l'option **Nom de colonne de la valeur de clé de tableau croisé dynamique** comme les valeurs de texte **Ham**, **Soda**, **Milk**, **Beer**et **Chips**.  
  
 **Nom de colonne de la valeur de clé de tableau croisé dynamique**  
 Tapez le nom de la colonne de valeur croisée dynamique. La valeur par défaut est « Valeur de clé de tableau croisé dynamique ». Toutefois, vous pouvez choisir un nom descriptif unique.  
  
 Dans le scénario Unpivot décrit dans [Unpivot Transformation](data-flow/transformations/unpivot-transformation.md), le nom de la colonne de la valeur de clé de tableau croisé dynamique est **Product** et définit la nouvelle colonne **Product** dans laquelle les colonnes **Ham**, **Soda**, **Milk**, **Beer**et **Chips** ne sont pas croisées dynamiquement.  
  
## <a name="see-also"></a>Voir aussi  
 [Integration Services Error and Message Reference](../../2014/integration-services/integration-services-error-and-message-reference.md)   
 [Transformation de tableau croisé dynamique](data-flow/transformations/pivot-transformation.md)  
  
  