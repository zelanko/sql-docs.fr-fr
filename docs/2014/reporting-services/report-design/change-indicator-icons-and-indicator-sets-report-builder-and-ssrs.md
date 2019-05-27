---
title: Changer les icônes d’indicateur et jeux d’indicateurs (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 8a056adf-4473-473d-9b0c-314675af7bfd
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 37f3b93019a837ac5521c52e9ceb5f58f3e39b5d
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66106371"
---
# <a name="change-indicator-icons-and-indicator-sets-report-builder-and-ssrs"></a>Modifier les icônes d'indicateur et jeux d'indicateurs (Générateur de rapports et SSRS)
  [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] Fournit des jeux d’indicateurs préconfigurés, qui ne peut pas toujours représenter efficacement vos données et fonctionnent correctement dans le rapport remis. Cette rubrique fournit des procédures permettant de modifier l'apparence des icônes d'indicateur et les jeux d'indicateurs pour inclure plus ou moins d'icônes d'indicateur, ou d'autres icônes d'indicateur.  
  
 Les options telles que les couleurs peuvent être définies à l'aide d'expressions. Pour plus d’informations, consultez [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-change-the-color-of-an-indicator-icon"></a>Pour modifier la couleur d'une icône d'indicateur  
  
1.  Cliquez avec le bouton droit sur l’indicateur à modifier, puis cliquez sur **Propriétés de l’indicateur**.  
  
2.  Cliquez sur **Valeur et états** dans le volet gauche.  
  
3.  Cliquez sur la flèche vers le bas dans la colonne **Couleur** en regard de l’icône que vous souhaitez changer et cliquez sur la couleur à utiliser, **Aucune couleur**ou **Couleurs supplémentaires**.  
  
     Cliquez éventuellement sur le bouton **Expression** (*fx*) pour modifier une expression qui définit la valeur de l’option **Couleur** .  
  
     Si vous avez cliqué sur **Couleurs supplémentaires**, la boîte de dialogue **Sélectionner une couleur** s’ouvre, dans laquelle vous pouvez choisir parmi un grand nombre de couleurs. Pour plus d’informations sur ses options, consultez [Boîte de dialogue Sélectionner une couleur &#40;Générateur de rapports et SSRS&#41;](../select-color-dialog-box-report-builder-and-ssrs.md). Cliquez sur **OK** pour fermer la boîte de dialogue **Sélectionner une couleur** .  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-change-the-icon"></a>Pour modifier l'icône  
  
1.  Cliquez avec le bouton droit sur l’indicateur à modifier, puis cliquez sur **Propriétés de l’indicateur**.  
  
2.  Cliquez sur **Valeur et états** dans le volet gauche.  
  
3.  Cliquez sur la flèche vers le bas en regard de l'icône que vous souhaitez changer et sélectionnez une icône différente.  
  
     Cliquez éventuellement sur le bouton **Expression** (*fx*) pour modifier une expression qui définit la valeur de l’option **Icône** .  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-use-a-custom-image-as-an-indicator-icon"></a>Pour utiliser une image personnalisée comme icône d'indicateur  
  
1.  Cliquez avec le bouton droit sur l’indicateur à modifier, puis cliquez sur **Propriétés de l’indicateur**.  
  
2.  Cliquez sur **Valeur et états** dans le volet gauche.  
  
3.  Cliquez sur la flèche vers le bas en regard de l’icône que vous souhaitez changer et sélectionnez **Image**.  
  
4.  Dans la liste **Sélectionner la source de l’image** , cliquez sur **Externe**, **Rapport**ou **Base de données**.  
  
5.  Selon la source de l'image, procédez de l'une des manières suivantes :  
  
    -   Pour utiliser une image stockée hors du rapport, cliquez sur **Parcourir** et recherchez l’image. Le rapport inclura une référence à l'image.  
  
    -   Pour utiliser une image incorporée dans le rapport, cliquez sur **Importer** et recherchez l’image. L'image sera ajoutée à la définition de rapport et enregistrée avec celle-ci.  
  
    -   Pour utiliser une image qui est dans une base de données, dans la liste **Utiliser ce champ** , sélectionnez le champ de la liste, puis dans la liste **Utiliser ce type MIME** , sélectionnez le type MIME de l’image.  
  
6.  Cliquez sur **OK**.  
  
### <a name="to-add-an-icon-to-the-indicator-set"></a>Pour ajouter une icône au jeu d'indicateurs  
  
1.  Cliquez avec le bouton droit sur l’indicateur à modifier, puis cliquez sur **Propriétés de l’indicateur**.  
  
2.  Cliquez sur **Valeur et états** dans le volet gauche.  
  
3.  Cliquez sur **Ajouter**. Un indicateur est ajouté, à l’aide de l’icône par défaut et de l’option **Aucune couleur** .  
  
     Configurez l'indicateur pour utiliser l'icône et la couleur souhaitées. Les procédures plus haut dans cette rubrique décrivent les étapes de cette opération.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-delete-an-icon-to-the-indicator-set"></a>Pour supprimer une icône du jeu d'indicateurs  
  
1.  Cliquez avec le bouton droit sur l’indicateur à modifier, puis cliquez sur **Propriétés de l’indicateur**.  
  
2.  Cliquez sur **Valeur et états** dans le volet gauche.  
  
3.  Sélectionnez l’icône à supprimer, puis cliquez sur **Supprimer**.  
  
4.  Cliquez sur **OK**.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs &#40;Générateur de rapports et SSRS&#41;](indicators-report-builder-and-ssrs.md)  
  
  
