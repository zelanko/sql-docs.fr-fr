---
title: Spécifier une Image en tant que pointeur sur une jauge (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 9d73b3c3-a068-4868-a2be-0cd261b6e92b
author: maggiesmsft
ms.author: douglasl
manager: craigg
ms.openlocfilehash: 2e2fbf2593ae5f85e12555d469ebe77b11539a20
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48178879"
---
# <a name="specify-an-image-as-a-pointer-on-a-gauge-report-builder-and-ssrs"></a>Spécifier une image en tant que pointeur dans une jauge (Générateur de rapports et SSRS)
  La jauge contient trois styles intégrés pouvant être utilisés pour personnaliser l'apparence du pointeur. Pour une jauge radiale, les styles intégrés sont les suivants : Aiguille, Marqueur et Barre. Pour une jauge linéaire, les styles intégrés sont les suivants : Marqueur, Barre et Thermomètre. Si un pointeur unique est requis, l'utilisateur peut créer et spécifier une image qui sera utilisée en tant que pointeur totalement fonctionnel.  
  
 Lorsque vous spécifiez une image pour le pointeur, celle-ci doit avoir les spécifications suivantes :  
  
-   L'origine du pointeur, ou centre de rotation, doit être située en haut de l'image.  
  
-   L'extrémité du pointeur doit pointer vers le bas.  
  
 Puisque le pointeur est de forme irrégulière, vous devrez spécifier une couleur transparente pour masquer les parties inutiles de l'image. Envisagez d'utiliser une couleur transparente qui n'est normalement pas affichée sur la jauge, étant donné que les couleurs spécifiées n'apparaîtront pas sur la jauge.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-specify-an-image-as-a-pointer-on-the-gauge"></a>Pour spécifier une image en tant que pointeur sur la jauge  
  
1.  En mode Conception, cliquez sur le pointeur de la jauge.  
  
2.  (Facultatif) Si aucun pointeur n’existe sur la jauge, avec le bouton droit sur la jauge et sélectionnez **ajouter un pointeur**. Un pointeur est ajouté à la jauge.  
  
3.  Cliquez sur le **insérer** onglet sur le ruban et double-cliquez sur l’icône d’image. La boîte de dialogue **Propriétés de l’image** s’ouvre.  
  
4.  Ajoutez une image à votre rapport. Pour plus d’informations, consultez [incorporer une Image dans un rapport &#40;Générateur de rapports et SSRS&#41;](report-design/embed-an-image-in-a-report-report-builder-and-ssrs.md).  
  
5.  Ouvrez le volet Propriétés.  
  
6.  Sur l'aire de conception, cliquez sur le pointeur. Les propriétés du pointeur sont affichées dans le volet Propriétés.  
  
7.  Développez le nœud PointerImage.  
  
8.  Dans **Source**, sélectionnez **Embedded** dans la liste déroulante.  
  
    > [!NOTE]  
    >  Si votre image est stockée dans la base de données ou sur le web, vous pouvez spécifier l'option appropriée pour cette propriété. Pour plus d’informations, consultez [boîte de dialogue de propriétés Image, général &#40;Générateur de rapports et SSRS&#41;](../../2014/reporting-services/image-properties-dialog-box-general-report-builder-and-ssrs.md).  
  
9. Dans **valeur**, sélectionnez le nom de votre image dans la liste déroulante.  
  
10. Dans **couleur transparente**, choisissez une couleur que vous souhaitez supprimer de l’image. Cette opération donne au pointeur de la jauge une apparence transparente.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des pointeurs sur une jauge &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Ajouter une jauge à un rapport &#40;Générateur de rapports et SSRS&#41;](report-design/add-a-gauge-to-a-report-report-builder-and-ssrs.md)   
 [Mise en forme des lignes, des couleurs et des images &#40;Générateur de rapports et SSRS&#41;](report-design/images-report-builder-and-ssrs.md)   
 [Jauges &#40;Générateur de rapports et SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
