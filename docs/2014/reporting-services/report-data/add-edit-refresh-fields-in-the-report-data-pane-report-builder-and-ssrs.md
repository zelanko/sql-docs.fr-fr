---
title: Ajouter, modifier ou actualiser des champs dans le volet Données du rapport (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
ms.assetid: 2e36f0fe-8100-4513-b169-14d611646f81
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: d5d243ef273badd182066fcc42484fa95fa13461
ms.sourcegitcommit: b87d36c46b39af8b929ad94ec707dee8800950f5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/08/2020
ms.locfileid: "66107488"
---
# <a name="add-edit-refresh-fields-in-the-report-data-pane-report-builder-and-ssrs"></a>ajouter, modifier ou actualiser des champs dans le volet des données de rapport (Générateur de rapports et SSRS)
  Les champs de dataset sont la collection intégrée de noms de champs qui représentent les données qui sont retournées lorsqu'une requête de dataset s'exécute sur une source de données externe.  
  
 Pour un dataset incorporé, les champs de dataset sont les champs créés après avoir terminé la génération d'une requête et fermé le volet Concepteur de requêtes, ainsi que les champs calculés que vous créez.  
  
 Pour un dataset partagé, les champs de dataset sont les champs de la définition du dataset partagé lorsque vous l'avez ajoutée à votre rapport. Bien que la requête depuis le dataset partagé sur le serveur de rapports soit toujours utilisée lorsque vous exécutez le rapport, la liste de champs de dataset est statique dans le rapport.  
  
 Utilisez **Actualiser les champs** pour mettre à jour la liste de champs dans le rapport afin qu'elle corresponde à la liste actuelle des champs de la requête du dataset partagé. L'actualisation de la liste de champs n'affecte pas les champs calculés que vous définissez dans votre rapport.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
### <a name="to-add-a-query-field"></a>Pour ajouter un champ de requête  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis sélectionnez **Ajouter un champ de requête**.  
  
    > [!NOTE]  
    >  Si le volet des données de rapport n’est pas visible, cliquez sur **Données du rapport** dans le menu **Affichage**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur **Ajouter**, puis sur **Champ de requête**. Une nouvelle ligne est ajoutée au bas de la grille.  
  
3.  Dans la zone de texte **Nom du champ** , tapez le nom du champ.  
  
    > [!NOTE]  
    >  Les noms doivent être uniques dans le dataset.  
  
4.  Dans la zone de texte **Champ source** , tapez le nom d'un champ existant sur la source de données.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-add-a-calculated-field"></a>Pour ajouter un champ calculé  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis cliquez sur **Ajouter un champ calculé**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur **Ajouter**, puis sur **Champ calculé**. Une nouvelle ligne est ajoutée au bas de la grille.  
  
3.  Dans la zone de texte **Nom du champ** , tapez le nom du champ.  
  
    > [!NOTE]  
    >  Les noms doivent être uniques dans le dataset.  
  
4.  Dans la zone de texte **Champ source** , tapez l'expression du champ. Cliquez sur le bouton d’expression (**fx**) pour générer une expression.  
  
    > [!NOTE]  
    >  L'expression d'un champ calculé ne peut contenir ni agrégations, ni références à des éléments de rapport.  
  
5.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-edit-a-query-field-or-a-dataset-field"></a>Pour modifier un champ de requête ou un champ de dataset  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le champ, puis cliquez sur **Propriétés du champ**.  
  
2.  Dans la page **Champs** de la boîte de dialogue **Propriétés du dataset** , cliquez sur un champ existant pour sélectionner la ligne.  
  
3.  Modifiez le nom ou la valeur du champ.  
  
4.  [!INCLUDE[clickOK](../../includes/clickok-md.md)]  
  
### <a name="to-delete-a-query-field-or-a-calculated-field"></a>Pour supprimer un champ de requête ou un champ calculé  
  
1.  Dans le volet des données de rapport, développez le dataset pour afficher la collection de champs.  
  
2.  Cliquez avec le bouton droit sur le champ à supprimer, puis sélectionnez **Supprimer**.  
  
### <a name="to-refresh-the-field-collection-in-the-report-data-pane-for-a-shared-dataset"></a>Pour actualiser la collection de champs dans le volet des données de rapport d'un dataset partagé  
  
1.  Dans le volet des données de rapport, cliquez avec le bouton droit sur le dataset, puis cliquez sur **Requête**.  
  
2.  Cliquez sur **Actualiser les champs**.  
  
     Sur le serveur de rapports, la requête du dataset partagé exécute et retourne la collection de champs actuelle.  
  
## <a name="see-also"></a>Voir aussi  
 [Collection de champs de dataset &#40;Générateur de rapports et SSRS&#41;](dataset-fields-collection-report-builder-and-ssrs.md)   
 [Ajouter des données à un rapport &#40;Générateur de rapports et SSRS&#41;](report-datasets-ssrs.md)   
 [Datasets incorporés dans le rapport et datasets partagés &#40;Générateur de rapports et SSRS&#41;](report-embedded-datasets-and-shared-datasets-report-builder-and-ssrs.md)   
 [Concepteurs de requêtes Reporting Services](../reporting-services-query-designers.md)   
 [Concepteurs de requêtes &#40;Générateur de rapports&#41;](../query-designers-report-builder.md)  
  
  
