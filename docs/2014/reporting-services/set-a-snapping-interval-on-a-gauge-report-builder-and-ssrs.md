---
title: Définir un intervalle d’alignement sur une jauge (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 0ece7297-6e2f-47fb-835d-b9e9cce53fe2
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 3e2a35e4d6fefb6830774ffd7b2c3bc13a5e097c
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66101366"
---
# <a name="set-a-snapping-interval-on-a-gauge-report-builder-and-ssrs"></a>Définir un intervalle d'alignement sur une jauge (Générateur de rapports et SSRS)
  Un intervalle d'alignement définit le multiple auquel les valeurs sont arrondies. Par défaut, la jauge pointera sur la valeur exacte du champ que vous avez spécifiée dans le volet des données. Toutefois, vous pouvez arrondir la valeur exacte vers le haut ou vers le haut afin que le pointeur s’aligne sur un intervalle prédéfini. Par exemple, si la valeur sur votre jauge est 34,2 et que vous spécifiez un intervalle d'alignement de 5, le pointeur de jauge pointera sur 35. Si la valeur sur votre jauge est 31,2 et que vous spécifiez un intervalle d'alignement de 5, le pointeur de jauge pointera sur 30.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../includes/ssrbrddup-md.md)]  
  
### <a name="to-set-a-snapping-interval-on-a-gauge"></a>Pour définir un intervalle d'alignement sur une jauge  
  
1.  Cliquez n'importe où sur les numéros de la jauge pour mettre en surbrillance l'échelle.  
  
2.  Ouvrez le volet Propriétés.  
  
    > [!NOTE]  
    >  Si vous ne voyez pas le volet Propriétés, cliquez sur l’onglet **affichage** , puis activez la case à cocher **Propriétés** .  
  
3.  Dans la propriété **pointeurs** , cliquez sur le bouton (...). L'Éditeur de collections du pointeur s'ouvre.  
  
4.  Affectez **** à `True`la propriété SnappingEnabled la valeur.  
  
5.  Définissez **SnappingInterval** sur une valeur qui représente l’intervalle d’alignement. Le pointeur sera aligné sur le multiple rond le plus proche de la valeur que vous avez spécifiée.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme des échelles sur une jauge &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-scales-on-a-gauge-report-builder-and-ssrs.md)   
 [Mise en forme des pointeurs sur une jauge &#40;Générateur de rapports et SSRS&#41;](report-design/formatting-pointers-on-a-gauge-report-builder-and-ssrs.md)   
 [Jauges &#40;Générateur de rapports et SSRS&#41;](report-design/gauges-report-builder-and-ssrs.md)  
  
  
