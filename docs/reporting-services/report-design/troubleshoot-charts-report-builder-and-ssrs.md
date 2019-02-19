---
title: Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS) | Microsoft Docs
ms.date: 01/17/2018
ms.prod: reporting-services
ms.prod_service: reporting-services-sharepoint, reporting-services-native
ms.technology: report-design
ms.topic: conceptual
ms.assetid: 3a327ffa-3b69-40d6-8015-cc01cfae9161
author: markingmyname
ms.author: maghan
ms.openlocfilehash: 3f90827cfd1cde13cfdbea730954bd29158e96db
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56286057"
---
# <a name="troubleshoot-charts-report-builder-and-ssrs"></a>Résoudre les problèmes liés aux graphiques (Générateur de rapports et SSRS)
  Ces problèmes peuvent être utiles lors de l'utilisation de graphiques.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="why-does-my-chart-count-not-sum-the-values-on-the-value-axis"></a>Pourquoi est-ce que mon graphique compte, au lieu d'additionner, les valeurs sur l'axe des ordonnées ?  
 La plupart des types de graphiques requièrent des valeurs numériques le long de l'axe des ordonnées, qui est en général l'axe des Y, pour qu'ils se dessinent correctement. Si le type de données du champ de valeur est **String**, le graphique ne peut pas afficher de valeur numérique, y compris en présence de chiffres dans les champs. À la place, le graphique affiche le nombre total de lignes qui contiennent une valeur dans ce champ. Pour éviter ce problème, assurez-vous que les champs que vous utilisez pour les séries de valeurs sont destinés à contenir des données numériques, par opposition aux champs de chaîne qui sont destinés à contenir des nombres mis en forme.  

## <a name="need-more-help"></a>Besoin d’aide ?  
   
  Voici quelques pistes :  
 * [SQL Server Reporting Services](https://stackoverflow.com/questions/tagged/reporting-services) sur Stack Overflow  
 * Signalez un problème ou faites une suggestion sur [Microsoft SQL Server UserVoice](https://feedback.azure.com/forums/908035-sql-server).  
  
## <a name="see-also"></a> Voir aussi  
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](../../reporting-services/report-design/charts-report-builder-and-ssrs.md)  
  
  
