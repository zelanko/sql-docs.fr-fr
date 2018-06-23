---
title: Analyser dans Excel (onglet navigateur, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Documents Microsoft
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- analysis-services
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- sql12.asvs.cubeeditor.browsecube.datapane.f1
- sql12.asvs.ssms.analyzeinexcel.f1
ms.assetid: 890ed457-137e-44ac-9b2c-83344a1b8fc9
caps.latest.revision: 22
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: b6e20d95fc7d1a097f50eb5cca4937cc62580ef3
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140210"
---
# <a name="analyze-in-excel-browser-tab-cube-designer-analysis-services---multidimensional-data"></a>Analyser dans Excel (onglet Explorateur, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  La fonctionnalité**Analyser dans Excel** permet au développeur du cube de vérifier rapidement la façon dont un projet est présenté à l'utilisateur final. La fonctionnalité **Analyser dans Excel** ouvre l'application Microsoft Excel, crée une connexion de source de données à la base de données de l'espace de travail, puis ajoute automatiquement un tableau croisé dynamique à la feuille de calcul. Cette fonction remplace le composant Office Web Control qui fournissait un tableau croisé dynamique incorporé dans l'onglet Navigateur dans les versions précédentes.  
  
 **Pour afficher les données du cube :**  
  
1.  Dans [!INCLUDE[ssBIDevStudio](../includes/ssbidevstudio-md.md)], dans l’Explorateur de solutions, double-cliquez sur un cube pour l’ouvrir dans le Concepteur de cube.  
  
2.  Cliquez sur l'onglet **Navigateur** .  
  
3.  Cliquez sur **Reconnecter** pour valider la connexion.  
  
4.  Cliquez sur l'icône Excel dans la barre de menus.  
  
5.  Cliquez sur **Activer**lorsque vous êtes invité à activer les connexions de données. Excel s'ouvre en utilisant la connexion de données active et ajoute un tableau croisé dynamique à la feuille de calcul afin que vous puissiez commencer à parcourir vos données.  
  
 Vous pouvez à présent générer un tableau croisé dynamique de façon interactive en faisant glisser des mesures de la table des faits vers la zone des valeurs, et des attributs de dimension vers les zones Ligne et Colonne. Si vous avez des hiérarchies, ajoutez-les aux zones Ligne ou Colonne. Vous pouvez réduire ou développer la hiérarchie pour parcourir les données de faits à des niveaux différents.  
  
 Les objets et les données sont affichés dans le contexte du rôle ou de l'utilisateur effectif et de la perspective. Lorsque vous utilisez Excel, les informations d'identification de l'utilisateur actuel, et non celles spécifiées dans la page **Informations d'emprunt d'identité** , sont utilisées pour la connexion à la source de données lorsqu'une requête est exécutée.  
  
> [!NOTE]  
>  Pour utiliser la fonctionnalité Analyser dans Excel, Excel doit être installé sur le même ordinateur que [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]. Si Excel n'est pas installé sur le même ordinateur, vous pouvez utiliser Excel sur un autre ordinateur et vous connecter au cube comme source de données. Vous pouvez ensuite ajouter manuellement un tableau croisé dynamique à la feuille de calcul. Les objets de modèle (tables, colonnes, mesures et KPI) sont inclus en tant que champs dans la liste de champs du tableau croisé dynamique.  
  
 Pour plus d'informations sur la fonctionnalité **Analyser dans Excel** , consultez ces ressources.  
  
 [Analyser dans Excel &#40;SSAS tabulaire&#41;](tabular-models/analyze-in-excel-ssas-tabular.md)  
  
 [Analyser un modèle tabulaire dans Excel &#40;SSAS tabulaire&#41;](tabular-models/analyze-a-tabular-model-in-excel-ssas-tabular.md)  
  
 [Parcourir les données et métadonnées de cube](multidimensional-models/browse-data-and-metadata-in-cube.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Navigateur &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](browser-cube-designer-analysis-services-multidimensional-data.md)   
 [Barre d’outils &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](toolbar-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Métadonnées &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](metadata-browser-tab-cube-designer-analysis-services-multidimensional-data.md)   
 [Interroger et filtrer &#40;onglet navigateur, Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](query-filter-browser-cube-designer-analysis-services-multidimensional-data.md)  
  
  