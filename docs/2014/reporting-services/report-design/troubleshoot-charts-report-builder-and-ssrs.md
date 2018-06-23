---
title: Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: b5369ef0fd3f96345e0fc7e0c688f1230bfe41c1
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36139744"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS)
  Ces problèmes peuvent être utiles lors de l'utilisation de graphiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Pourquoi est-ce que mon graphique compte, au lieu d'additionner, les valeurs sur l'axe des ordonnées ?  
 La plupart des types de graphiques requièrent des valeurs numériques le long de l'axe des ordonnées, qui est en général l'axe des Y, pour qu'ils se dessinent correctement. Si le type de données du champ de valeur est `String`, le graphique ne peut pas afficher une valeur numérique, même s’il existe des chiffres dans les champs. À la place, le graphique affiche le nombre total de lignes qui contiennent une valeur dans ce champ. Pour éviter ce problème, assurez-vous que les champs que vous utilisez pour les séries de valeurs sont destinés à contenir des données numériques, par opposition aux champs de chaîne qui sont destinés à contenir des nombres mis en forme.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;rapport Générateur et SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  