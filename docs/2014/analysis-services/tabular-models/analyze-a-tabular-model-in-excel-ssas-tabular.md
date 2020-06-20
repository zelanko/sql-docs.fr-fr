---
title: Analyser un modèle tabulaire dans Excel (SSAS tabulaire) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.bidtoolset.chooseperspect.f1
ms.assetid: 47fa45fc-60ab-41a1-bde3-5781c8462889
author: minewiskan
ms.author: owend
ms.openlocfilehash: 36b28a97b920e5c43644451ebee1e0c50df019c2
ms.sourcegitcommit: 9ee72c507ab447ac69014a7eea4e43523a0a3ec4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "84939933"
---
# <a name="analyze-a-tabular-model-in-excel-ssas-tabular"></a>Analyser un modèle tabulaire dans Excel (SSAS Tabulaire)
  La fonctionnalité Analyser dans Excel de [!INCLUDE[ssBIDevStudioFull](../../includes/ssbidevstudiofull-md.md)] ouvre l’application Microsoft Excel, crée une connexion de source de données à la base de données model de l’espace de travail, puis ajoute un tableau croisé dynamique à la feuille de calcul. Les objets de modèle (tables, colonnes, mesures, hiérarchies et KPI) sont inclus en tant que champs dans la liste de champs du tableau croisé dynamique.  
  
> [!NOTE]  
>  Pour utiliser la fonctionnalité Analyser dans Excel, vous devez disposer de Microsoft Office 2003 ou d’une version ultérieure installée sur le même ordinateur que [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)]. Si Office n'est pas installé sur le même ordinateur, vous pouvez utiliser Excel sur un autre ordinateur et vous connecter à la base de données model de l'espace de travail comme source de données. Vous pouvez ensuite ajouter manuellement un tableau croisé dynamique à la feuille de calcul. Les objets de modèle (tables, colonnes, mesures et KPI) sont inclus en tant que champs dans la liste de champs du tableau croisé dynamique.  
  
## <a name="tasks"></a>Tâches  
  
#### <a name="to-analyze-a-tabular-model-project-by-using-the-analyze-in-excel-feature"></a>Pour analyser un projet de modèle tabulaire à l'aide de la fonctionnalité Analyser dans Excel  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../../includes/ssbidevstudio-md.md)], cliquez sur le menu **Modèle** , puis sur **Analyser dans Excel**.  
  
2.  Dans la boîte de dialogue **Choisir les informations d’identification et la perspective** , sélectionnez l’une des options relatives aux informations d’identification suivantes pour vous connecter à la source de données de l’espace de travail du modèle :  
  
    -   Pour utiliser le compte d’utilisateur actuel, sélectionnez **Utilisateur Windows actuel**.  
  
    -   Pour utiliser un compte d’utilisateur différent, sélectionnez **Autre utilisateur Windows**.  
  
         En général, ce compte d'utilisateur est membre d'un rôle. Aucun mot de passe n'est requis. Le compte ne peut être utilisé que dans le contexte d'une connexion Excel à la base de données d'espace de travail.  
  
    -   Pour utiliser un rôle de sécurité, sélectionnez **Rôle**puis, dans la zone de liste, sélectionnez un ou plusieurs rôles.  
  
         Les rôles de sécurité doivent être définis à l'aide du gestionnaire de rôles. Pour plus d’informations, consultez [Créer et gérer des rôles &#40;SSAS Tabulaire&#41;](roles-ssas-tabular.md).  
  
3.  Pour utiliser une perspective, dans la zone de liste **Perspective** , sélectionnez une perspective.  
  
     Les perspectives (autres que celles par défaut) doivent être définies à l'aide de la boîte de dialogue Perspectives. Pour plus d’informations, consultez [créer et gérer des Perspectives &#40;&#41;tabulaires SSAS ](perspectives-ssas-tabular.md).  
  
> [!NOTE]  
>  La liste de champs du tableau croisé dynamique dans Excel n'est pas actualisée automatiquement lorsque vous apportez des modifications au projet de modèle dans le générateur de modèles. Pour actualiser la liste de champs du tableau croisé dynamique, dans Excel, dans le ruban **Options** , cliquez sur **Actualiser**.  
  
## <a name="see-also"></a>Voir aussi  
 [Analyser dans Excel &#40;SSAS Tabulaire&#41;](analyze-in-excel-ssas-tabular.md)  
  
  
