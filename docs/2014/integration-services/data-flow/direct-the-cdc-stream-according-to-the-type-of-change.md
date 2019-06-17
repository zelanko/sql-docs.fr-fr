---
title: Diriger le flux de capture de données modifiées en fonction du type de modification | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
ms.assetid: 3afa531e-f425-40a4-a1bf-1c3e1727287e
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: 2ee2b3238a66000546619815a886fc6017c51fe6
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "62827399"
---
# <a name="direct-the-cdc-stream-according-to-the-type-of-change"></a>Diriger le flux de capture de données modifiées en fonction du type de modification
  Pour pouvoir ajouter et configurer une transformation de séparateur de capture de données modifiées, le package doit contenir au moins une tâche de flux de données et une source CDC.  
  
 La source CDC ajoutée au package doit avoir un mode de traitement NetCDC sélectionné. Pour plus d’informations sur la sélection des modes de traitement, consultez [Éditeur de source CDC &#40;page Gestionnaire de connexions&#41;](../cdc-source-editor-connection-manager-page.md).  
  
### <a name="to-direct-the-cdc-stream-according-to-the-type-of-change"></a>Pour diriger le flux de données de capture de données modifiées en fonction du type de modification  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], ouvrez le projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] contenant le package souhaité.  
  
2.  Dans l’Explorateur de solutions, double-cliquez sur le package pour l’ouvrir.  
  
3.  Cliquez sur l'onglet **Flux de données** , puis dans la **Boîte à outils**, faites glisser le séparateur de capture de données modifiées sur l'aire de conception.  
  
4.  Connectez la source CDC incluse dans le package au séparateur de capture de données modifiées.  
  
5.  Connectez le séparateur de capture de données modifiées à une ou plusieurs destinations. vous pouvez connecter jusqu'à trois sorties différentes.  
  
6.  Sélectionnez l'une des sorties suivantes :  
  
    -   Sortie de suppression : Sortie vers laquelle les lignes de modification DELETE sont dirigées.  
  
    -   Sortie d’insertion : Sortie vers laquelle les lignes de modification INSERT sont dirigées.  
  
    -   Sortie de mise à jour : Sortie vers laquelle les lignes de modification avant/après UPDATE et les lignes de modification MERGE sont dirigées.  
  
7.  Éventuellement, vous pouvez configurer les propriétés avancées à l'aide de la boîte de dialogue **Éditeur avancé** .  
  
     La boîte de dialogue **Éditeur avancé** contient les propriétés qui peuvent être définies par programmation.  
  
     Pour ouvrir la boîte de dialogue **Éditeur avancé** :  
  
    -   Sur l'écran **Flux de données** de votre projet [!INCLUDE[ssISCurrent](../../includes/ssiscurrent-md.md)] , cliquez avec le bouton droit sur le séparateur de capture de données modifiées, puis sélectionnez **Afficher l'éditeur avancé**.  
  
     Pour plus d'informations sur l'utilisation du séparateur de capture de données modifiées, consultez Composants de capture de données modifiées pour Microsoft SQL Server Integration Services.  
  
## <a name="see-also"></a>Voir aussi  
 [Séparateur de capture de données modifiées](cdc-splitter.md)  
  
  
