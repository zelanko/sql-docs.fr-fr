---
title: Éditeur de transformation de copie de colonne | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
f1_keywords:
- sql12.dts.designer.copymaptransformation.f1
helpviewer_keywords:
- Copy Column Transformation Editor
ms.assetid: d8e70541-d563-4ce4-bf66-bc888a0d3026
author: chugugrace
ms.author: chugu
ms.openlocfilehash: 7647d25891b37e5f09356d427072e84b45882e4c
ms.sourcegitcommit: 34278310b3e005d008cd2106a7b86fc6e736f661
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2020
ms.locfileid: "85437966"
---
# <a name="copy-column-transformation-editor"></a>Éditeur de transformation de copie de colonne
  Utilisez la boîte de dialogue **Éditeur de transformation de copie de colonne** pour sélectionner des colonnes à copier et attribuer des noms aux nouvelles colonnes de sortie.  
  
 Pour en savoir plus sur la transformation de copie de colonne, consultez [Copy Column Transformation](data-flow/transformations/copy-column-transformation.md).  
  
> [!NOTE]  
>  Si vous copiez simplement toutes vos données sources vers une destination, l'utilisation de la transformation de copie de colonne peut ne pas être obligatoire. Dans certains scénarios, vous pouvez connecter une source directement à une destination, lorsque aucune transformation de données n'est requise. Dans ces circonstances, il est souvent préférable d'utiliser l'Assistant Importation et Exportation SQL Server pour créer votre package. Ultérieurement, vous pouvez améliorer et reconfigurer le package selon les besoins. Pour plus d'informations, consultez [SQL Server Import and Export Wizard](import-export-data/import-and-export-data-with-the-sql-server-import-and-export-wizard.md).  
  
## <a name="options"></a>Options  
 **Colonnes d’entrée disponibles**  
 Utilisez les cases à cocher pour sélectionner les colonnes à copier. Les sélections ajoutent des colonnes d'entrée à la table ci-dessous.  
  
 **Colonne d'entrée**  
 Sélectionnez dans la liste les colonnes d'entrée à copier. Vos sélections se reflètent dans les sélections des cases à cocher de la table **Colonnes d'entrée disponibles** .  
  
 **Alias de sortie**  
 Tapez un alias pour chaque nouvelle colonne de sortie. Le nom par défaut est **Copie de**suivi du nom de la colonne d'entrée ; vous pouvez néanmoins choisir un nom unique et descriptif.  
  
## <a name="see-also"></a>Voir aussi  
 [Guide de référence des erreurs et des messages propres à Integration Services](../../2014/integration-services/integration-services-error-and-message-reference.md)  
  
  
