---
title: Documentation des modèles d’exploration de données (compléments d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- documenting models
- mining structures, managing
- mining models, managing
- model properties
ms.assetid: 0a663e11-e40c-4708-ad18-fabb6c976fa4
author: minewiskan
ms.author: owend
ms.openlocfilehash: 92ed5c43fa2b7484485b915d42946121487386d9
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84528485"
---
# <a name="documenting-mining-models-data-mining-add-ins-for-excel"></a>Modèles de documentation de l'exploration de données (Compléments d'exploration de données pour Excel)
  ![Bouton Modèle de document, ruban Exploration de données](media/dmc-docmodel.gif "Bouton Modèle de document, ruban Exploration de données")  
  
 L’Assistant **modèle de document** crée un rapport qui fournit des informations utiles sur les modèles d’exploration de données que vous avez créés. En documentant les modèles que vous créez, vous pouvez effectuer le suivi de la source des données utilisée pour générer un modèle, obtenir des informations supplémentaires quant au moment où le modèle a été traité et assurer le suivi des modifications des paramètres qui affectent les résultats du modèle.  
  
## <a name="using-the-document-model-wizard"></a>Utilisation de l'Assistant Modèle de document  
  
1.  Cliquez sur l’onglet **exploration de données** .  
  
2.  Dans le groupe **utilisation du modèle** , cliquez sur modèle de **document**.  
  
3.  Dans la boîte de dialogue **Sélectionner le modèle** , sélectionnez le modèle sur lequel vous souhaitez effectuer le rapport, puis cliquez sur **suivant**. Vous devez exécuter l’Assistant **modèle de document** séparément pour chaque modèle que vous souhaitez documenter.  
  
4.  Dans la boîte de dialogue **Sélectionner les détails** de la documentation, choisissez l’une des deux options suivantes : **informations complètes** ou **informations résumées**.  
  
5.  Cliquez sur **Terminer**.  
  
6.  L’Assistant crée automatiquement une nouvelle feuille de calcul qui contient le rapport spécifié, intitulé **documentation du modèle**,  
  
## <a name="understanding-the-report"></a>Présentation du rapport  
 Lorsque vous créez un rapport qui documente un modèle d'exploration de données, vous pouvez créer un résumé contant des informations de base avec le nom et la description du modèle ou un rapport complet qui contient des détails sur la structure sous-jacente et des information avancées à propos du modèle d'exploration de données.  
  
 Selon l'algorithme utilisé pour créer le modèle, différents types d'informations sont fournis. Par exemple, dans un modèle d'association vous êtes davantage intéressé de connaître le nombre de jeux d'éléments et de règles qui été générés. Pour un modèle de clustering, le nombre de clusters est plus intéressant.  
  
 Le tableau suivant répertorie les options et les informations fournies dans le rapport pour chaque option.  
  
> [!NOTE]  
>  Les colonnes dans le rapport sont définies selon une taille particulière par défaut. Par conséquent, si des noms de colonnes ou valeurs sont très longs, ils peuvent ne pas être visibles ou peuvent apparaître comme ### dans Excel. Pour rendre les valeurs visibles, vous pouvez redimensionner la ligne. Si la cellule est sélectionnée, vous pouvez cliquer et faire glisser les flèches à deux pointes à la fin de la barre de formule pour afficher la valeur ou chaîne complète.  
  
### <a name="summary-report"></a>Rapport de résumé  
  
||||  
|-|-|-|  
|**Métadonnées**|Nom du modèle<br /><br /> Description du modèle<br /><br /> Nom de l'algorithme<br /><br /> Date du dernier traitement||  
|**Résultats du modèle**|Association|Nombre de jeux d'éléments<br /><br /> Nombre de règles|  
||Clustering|Nombre de clusters<br /><br /> Prise en charge pour chaque cluster|  
||Arbre de décision|Nombre d'arbres<br /><br /> Nombre de nœuds dans chaque arbre|  
||Régression linéaire|Nombre d'arbres (toujours 1)<br /><br /> Nombre de noeuds (toujours 1)|  
||Naïve Bayes|Attributs importants|  
||Réseau neuronal|Nombre de nœuds d'entrée<br /><br /> Nombre de nœuds de sortie<br /><br /> Nombre de nœuds masqués|  
||Sequence clustering|Nombre de clusters|  
  
### <a name="complete-report"></a>Rapport complet  
 Le rapport complet contient tout qui se trouve dans le rapport de résumé, plus des informations détaillées à propos des colonnes de données utilisées dans le modèle et les résultats d'analyse :  
  
||||  
|-|-|-|  
|**Métadonnées**|Métadonnées du modèle|Paramètres et valeurs de l'algorithme|  
||Métadonnées de colonne|Nom de la colonne<br /><br /> Usage<br /><br /> Type de données<br /><br /> Type de contenu<br /><br /> Valeurs (liste de valeurs discrètes, ou plage de valeurs)|  
|**Statistiques du modèle**|Colonnes continues|Valeur moyenne<br /><br /> Valeur minimale<br /><br /> Valeur maximale<br /><br /> Erreur du carré moyen racine<br /><br /> Erreur d'absolue moyenne<br /><br /> Score du journal<br /><br /> Formule de régression (uniquement pour les modèles de régression linéaire)|  
||Colonnes discrètes|Nombre de succès<br /><br /> Nombre d'échecs<br /><br /> Score du journal<br /><br /> Finesse|  
  
> [!NOTE]  
>  Vous pouvez documenter tout type modèle pris en charge par SQL Server Analysis Services. Par conséquent, le tableau répertorie certains types de modèles qui ne peuvent pas être créés à l'aide des outils d'analyse de table ou des Assistants du client d'exploration de données. Toutefois, vous pouvez créer tous les types de modèles à l’aide de l' **éditeur de requêtes d’exploration de données avancé**. Pour plus d’informations, consultez [&#40;des compléments d’exploration de données SQL Server&#41;](query-sql-server-data-mining-add-ins.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Déploiement et mise à l’échelle des modèles d’exploration de données &#40;les compléments d’exploration de données pour Excel&#41;](deploying-and-scaling-mining-models-data-mining-add-ins-for-excel.md)  
  
  
