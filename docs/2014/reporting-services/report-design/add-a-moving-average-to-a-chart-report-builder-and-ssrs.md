---
title: Ajouter une moyenne mobile à un graphique (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 166cf9c1-0750-4866-8381-542e4fbfe65a
author: markingmyname
ms.author: maghan
manager: kfile
ms.openlocfilehash: 7114291f64190207a48526a42976580b09933282
ms.sourcegitcommit: 31800ba0bb0af09476e38f6b4d155b136764c06c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56297195"
---
# <a name="add-a-moving-average-to-a-chart-report-builder-and-ssrs"></a>Ajouter une moyenne mobile à un graphique (Générateur de rapports et SSRS)
  Une moyenne mobile est une moyenne des données de votre série, calculée sur une période de temps définie. La moyenne mobile peut être indiquée sur le graphique pour identifier les tendances significatives.  
  
 La formule de moyenne mobile est l'indicateur de prix le plus populaire utilisé dans les analyses techniques. De nombreuses autres formules, y compris la moyenne, la médiane et l'écart type, peuvent également être dérivées d'une série sur le graphique. Lors de la spécification d'une moyenne mobile, chaque formule peut comporter un ou plusieurs paramètres qui doivent être spécifiés.  
  
 Lorsqu'une formule de moyenne mobile est ajoutée en mode Création, la série de lignes ajoutée est uniquement un espace réservé visuel. Le graphique calculera les points de données de chaque formule pendant le traitement des rapports.  
  
 La prise en charge intégrée des courbes de tendance n’est pas disponible dans [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)].  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-calculated-moving-average-to-a-series-on-the-chart"></a>Pour ajouter une moyenne mobile calculée à une série sur le graphique  
  
1.  Cliquez avec le bouton droit sur un champ dans la zone **Valeurs** , puis cliquez sur **Ajouter une série calculée**. La boîte de dialogue **Propriétés de la série calculée** s'ouvre.  
  
2.  Sélectionnez l’option **Moyenne mobile** dans la liste déroulante **Formule** .  
  
3.  Spécifiez une valeur entière pour la **Période** qui représente la période de la moyenne mobile.  
  
    > [!NOTE]  
    >  La période est le nombre de jours utilisés pour calculer une moyenne mobile. Si les valeurs de date/d'heure ne sont pas spécifiées sur l'axe des abscisses, la période est représentée par le nombre de points de données utilisés pour calculer une moyenne mobile. S'il n'existe qu'un seul point de données, la formule de moyenne mobile n'effectue pas de calcul. La moyenne mobile est calculée en commençant par le deuxième point. Si vous spécifiez l'option **Démarrer à partir du premier point** , le graphique démarrera la moyenne mobile au niveau du premier point. S'il n'existe qu'un seul point de données, le point dans la moyenne mobile calculée sera identique au premier point dans votre série d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Mise en forme d’un graphique &#40;Générateur de rapports et SSRS&#41;](formatting-a-chart-report-builder-and-ssrs.md)   
 [Graphiques &#40;Générateur de rapports et SSRS&#41;](charts-report-builder-and-ssrs.md)   
 [Ajouter des Points vides au graphique &#40;Générateur de rapports et SSRS&#41;](add-empty-points-to-a-chart-report-builder-and-ssrs.md)  
  
  
