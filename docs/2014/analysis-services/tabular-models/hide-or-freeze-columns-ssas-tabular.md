---
title: Masquer ou figer des colonnes (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.hideunhidecolumnsdb.f1
ms.assetid: 5407aee5-6a07-4559-a2ba-2ca00a242f02
caps.latest.revision: 9
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d3277c722652e67036d0c0bfe2a904797f327a4d
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37214049"
---
# <a name="hide-or-freeze-columns-ssas-tabular"></a>Masquer ou figer des colonnes (SSAS Tabulaire)
  Dans le générateur de modèles, s'il existe des colonnes que vous ne souhaitez pas afficher dans une table, vous pouvez les masquer temporairement. Masquer une colonne vous permet de disposer de plus d'espace à l'écran pour ajouter de nouvelles colonnes ou de travailler uniquement avec les colonnes contenant des données pertinentes. Vous pouvez masquer et afficher des colonnes à partir du menu **Colonne** dans le générateur de modèles ou à partir du menu contextuel disponible dans chaque en-tête de colonne. Pour garder une zone d'un modèle visible pendant que vous faites défiler le modèle jusqu'à une autre zone, vous pouvez verrouiller des colonnes spécifiques dans une zone en les figeant.  
  
> [!IMPORTANT]  
>  La possibilité de masquer des colonnes n'est pas liée à la sécurité des données, mais sert uniquement à simplifier et raccourcir la liste de colonnes visibles dans le générateur de modèles ou les rapports. Pour sécuriser des données, vous pouvez définir des rôles de sécurité. Les rôles peuvent limiter les métadonnées visibles et les données aux seuls objets définis dans le rôle. Pour plus d’informations, consultez [Roles &#40;SSAS Tabular&#41;](roles-ssas-tabular.md).  
  
 Quand vous masquez une colonne, vous pouvez masquer la colonne pendant que vous travaillez dans le générateur de modèles ou dans les rapports. Si vous masquez toutes les colonnes, la table entière apparaît vide dans le générateur de modèles.  
  
> [!NOTE]  
>  Si vous avez de nombreuses colonnes à masquer, vous pouvez créer une perspective au lieu de masquer et d'afficher des colonnes. Une perspective est une vue personnalisée des données qui simplifie l'utilisation d'un sous-ensemble de données associées. Pour plus d’informations, consultez [Créer et gérer des perspectives &#40;SSAS Tabulaire&#41;](perspectives-ssas-tabular.md).  
  
### <a name="to-hide-an-individual-column"></a>Pour masquer une colonne individuelle  
  
1.  Dans le générateur de modèles, sélectionnez la table contenant la colonne à masquer.  
  
2.  Cliquez avec le bouton droit sur la colonne, puis sélectionnez **Masquer les colonnes**, puis cliquez sur **Depuis le concepteur et les rapports**, **Depuis les rapports**ou **Depuis le concepteur**.  
  
### <a name="to-hide-multiple-columns"></a>Pour masquer plusieurs colonnes  
  
1.  Dans le générateur de modèles, sélectionnez la table contenant les colonnes à masquer.  
  
2.  Cliquez sur le menu **Colonnes** , puis sur **Masquer et afficher.**  
  
3.  Dans la boîte de dialogue **Masquer et afficher les colonnes** , recherchez le nom de chaque colonne que vous souhaitez masquer, puis désélectionnez **Dans le concepteur** et/ou **Dans les rapports**.  
  
4.  Cliquez sur **OK**.  
  
### <a name="to-freeze-columns"></a>Pour figer des colonnes  
  
1.  Dans le générateur de modèles, sélectionnez la table contenant les colonnes à figer.  
  
2.  Sélectionnez une ou plusieurs colonnes à figer.  
  
3.  Cliquez sur le menu **Colonnes** , puis sur **Figer**.  
  
    > [!NOTE]  
    >  Lorsqu'une colonne est figée, elle est déplacée vers la gauche (ou à l'avant) de la table dans le concepteur. Libérer la colonne ne la replace pas à son emplacement d'origine.  
  
## <a name="see-also"></a>Voir aussi  
 [Tables et colonnes &#40;SSAS tabulaire&#41;](tables-and-columns-ssas-tabular.md)   
 [Perspectives &#40;SSAS tabulaire&#41;](perspectives-ssas-tabular.md)   
 [Rôles &#40;SSAS tabulaire&#41;](roles-ssas-tabular.md)  
  
  
