---
title: Résoudre les problèmes liés aux graphiques (Générateur de rapports) | Microsoft Docs
description: Utilisez des champs avec des types de données numériques le long de l’axe des ordonnées plutôt que des nombres mis en forme pour afficher une valeur numérique.
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: maggiesMSFT
ms.author: maggies
ms.openlocfilehash: 45894eca20fa5762eb4f2e02496e79bd327c8fb3
ms.sourcegitcommit: 5b7457c9d5302f84cc3baeaedeb515e8e69a8616
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "83689467"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS)
  Ces problèmes peuvent être utiles lors de l'utilisation de graphiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Pourquoi est-ce que mon graphique compte, au lieu d'additionner, les valeurs sur l'axe des ordonnées ?  
 La plupart des types de graphiques requièrent des valeurs numériques le long de l'axe des ordonnées, qui est en général l'axe des Y, pour qu'ils se dessinent correctement. Si le type de données du champ de valeur est **String**, le graphique ne peut pas afficher de valeur numérique, y compris en présence de chiffres dans les champs. À la place, le graphique affiche le nombre total de lignes qui contiennent une valeur dans ce champ. Pour éviter ce problème, assurez-vous que les champs que vous utilisez pour les séries de valeurs sont destinés à contenir des données numériques, par opposition aux champs de chaîne qui sont destinés à contenir des nombres mis en forme.  

## <a name="need-more-help"></a>Besoin d’aide ?  
   
  Essayez de procéder comme suit :  
 * [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services) sur Stack Overflow  
 * Signalez un problème ou faites une suggestion sur [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a>Voir aussi  
 [Graphiques (Générateur de rapports et SSRS)](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
