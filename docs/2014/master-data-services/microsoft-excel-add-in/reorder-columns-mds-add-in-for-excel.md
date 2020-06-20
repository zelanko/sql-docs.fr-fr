---
title: Réorganiser des colonnes (Complément MDS pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: master-data-services
ms.topic: conceptual
ms.assetid: ac00462e-c0f7-4b8d-86f2-d9eda2598a15
author: lrtoyou1223
ms.author: lle
ms.openlocfilehash: 652ef1583173fa1f84a40d58a6d71f7f2a5f00f1
ms.sourcegitcommit: f71e523da72019de81a8bd5a0394a62f7f76ea20
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84960929"
---
# <a name="reorder-columns-mds-add-in-for-excel"></a>Réorganiser des colonnes (Complément MDS pour Excel)
  Dans [!INCLUDE[ssMDSshort](../../includes/ssmdsshort-md.md)][!INCLUDE[ssMDSXLS](../../includes/ssmdsxls-md.md)], vous pouvez réorganiser les colonnes en filtrant la liste avant le chargement.  
  
 Lorsque vous réorganisez les attributs dans la boîte de dialogue **Filtre** , les données sont chargées dans Excel dans le nouvel ordre. Toutefois, lors du prochain filtrage des données d'attribut, l'ordre rétabli sera celui de la conception d'origine. Pour modifier définitivement l'ordre, un administrateur doit modifier l'ordre dans la zone **Administration de système** de Master Data Manager. Pour plus d’informations, voir [Change the Order of Attributes](../change-the-order-of-attributes.md).  
  
## <a name="prerequisites"></a>Prérequis  
 Pour effectuer cette procédure :  
  
-   Vous devez avoir l'autorisation d'accéder à la zone fonctionnelle **Explorateur** .  
  
### <a name="to-reorder-mds-managed-columns"></a>Pour réorganiser les colonnes managées MDS  
  
1.  Ouvrez Excel et accédez à l'onglet **Données de référence** , puis connectez-vous à un référentiel MDS. Pour plus d’informations, consultez [Se connecter à un référentiel MDS &#40;complément MDS pour Excel&#41;](connect-to-an-mds-repository-mds-add-in-for-excel.md).  
  
2.  Dans le volet **Explorateur de données de référence** , sélectionnez un modèle et une version. La liste des entités est remplie.  
  
    -   Si le volet **Explorateur de données de référence** n'est pas visible, dans le groupe **Se connecter et charger** , cliquez sur **Afficher l'Explorateur**.  
  
    -   Si le volet **Explorateur de données de référence** est désactivé, cela signifie que la feuille de calcul existante contient déjà des données managées MDS. Pour activer le volet, ouvrez une nouvelle feuille de calcul.  
  
3.  Dans le volet **Explorateur de données de référence** , cliquez sur une entité.  
  
4.  Dans le groupe **Se connecter et charger** , cliquez sur **Filtrer**.  
  
5.  Dans la boîte de dialogue **Filtrer** , dans la section **Colonnes** , dans la liste d'attributs, cliquez sur l'attribut à déplacer.  
  
6.  À droite de la liste, cliquez sur la flèche **Haut** ou **Bas** pour déplacer l'attribut à gauche et à droite dans la feuille de calcul.  
  
7.  Répétez l'étape 7 pour chaque attribut jusqu'à ce que l'ordre de haut en bas représente l'ordre de gauche à droite que vous souhaitez dans la feuille de calcul.  
  
8.  Cliquez sur **Charger les données**. La feuille est renseignée avec les données managées MDS et les colonnes sont affichées dans l'ordre que vous avez spécifié.  
  
## <a name="see-also"></a>Voir aussi  
 [Chargement de données &#40;Complément MDS pour Excel&#41;](overview-exporting-data-to-excel-mds-add-in-for-excel.md)  
  
  
