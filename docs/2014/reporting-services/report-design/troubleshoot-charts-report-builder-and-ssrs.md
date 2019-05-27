---
title: Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: b931b50545ba2b8d7c4c06cc5c48d6415a05470a
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66104659"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS)
  Ces problèmes peuvent être utiles lors de l'utilisation de graphiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Pourquoi est-ce que mon graphique compte, au lieu d'additionner, les valeurs sur l'axe des ordonnées ?  
 La plupart des types de graphiques requièrent des valeurs numériques le long de l'axe des ordonnées, qui est en général l'axe des Y, pour qu'ils se dessinent correctement. Si le type de données du champ de valeur est `String`, le graphique ne peut pas afficher de valeur numérique, y compris en présence de chiffres dans les champs. À la place, le graphique affiche le nombre total de lignes qui contiennent une valeur dans ce champ. Pour éviter ce problème, assurez-vous que les champs que vous utilisez pour les séries de valeurs sont destinés à contenir des données numériques, par opposition aux champs de chaîne qui sont destinés à contenir des nombres mis en forme.  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)  
  
  
