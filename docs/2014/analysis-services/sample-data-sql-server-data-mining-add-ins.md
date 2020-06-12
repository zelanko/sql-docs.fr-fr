---
title: Exemples de données (compléments d’exploration de données SQL Server) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- mining models, validating
- holdout
- testing cases
- training cases
- partitioning data [data mining]
- mining models, testing
ms.assetid: 35907ae6-887f-4cb3-a750-cff3d7683d90
author: minewiskan
ms.author: owend
ms.openlocfilehash: eb8c0f9424c9e817ee482f426b3045e878a9c9c9
ms.sourcegitcommit: f0772f614482e0b3cde3609e178689ce62ca3a19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84539061"
---
# <a name="sample-data-sql-server-data-mining-add-ins"></a>Exemples de données (Compléments d'exploration de données SQL Server)
  ![Assistant Partition des données sur le ruban Exploration de données](media/dmc-partition.gif "Assistant Partition des données sur le ruban Exploration de données")  
  
 L’Assistant **exemples de données** permet de diviser facilement vos données sources en deux jeux : un pour la création (apprentissage) du modèle et l’autre pour tester le modèle. Cet Assistant fournit également une option pour rééchantillonner les données en vue de générer un nouveau jeu de données qui représente mieux votre cible.  
  
 La création du type de données correct pour l'apprentissage et le test de vos modèles constitue une part importante de l'exploration de données, mais cette tâche peut être fastidieuse si vous ne disposez pas des outils adéquats. L'Assistant effectue un échantillonnage stratifié pour garantir que les jeux de test et d'apprentissage sont bien équilibrés.  
  
## <a name="random-sampling-and-oversampling"></a>Échantillonnage aléatoire et suréchantillonnage  
 . L'échantillonnage aléatoire est la meilleure méthode pour garantir que les données que vous utilisez pour tester un modèle représentent réellement les données que vous utilisez pour créer le modèle. Échantillonnez de façon aléatoire des données stockées dans Excel ou dans une source de données externe.  
  
 Si vous utilisez l’option d’échantillonnage aléatoire, l’Assistant **exemples de données** crée automatiquement des jeux de données d’apprentissage et de test et les génère dans des feuilles de calcul Excel distinctes pour une référence ultérieure.  
  
 Si vos données sont stockées dans un classeur Excel et non dans une source de données externe, vous avez également la possibilité d’utiliser le *suréchantillonnage*. Avec cette option, vous spécifiez une valeur cible qui peut être rare dans vos données et l'Assistant recueille un jeu équilibré qui contient un plus grand nombre de valeurs cibles. Indiquez à l'Assistant d'atteindre un pourcentage ciblé ou de créer un certain nombre de lignes.  
  
 Si vous utilisez l’option de suréchantillonnage, l’Assistant **exemples de données** crée une feuille de calcul qui contient les exemples de données qui viennent d’être équilibrées.  
  
## <a name="using-the-sample-data-wizard"></a>Utilisation de l'Assistant Exemples de données  
  
#### <a name="to-separate-data-into-training-and-testing-sets"></a>Pour diviser les données en jeux d'apprentissage et de test  
  
1.  Dans le ruban **exploration de données** , cliquez sur exemples de **données**.  
  
2.  Dans la page **Sélectionner les données sources** , spécifiez si les **données** que vous souhaitez partitionner se trouvent dans une plage ou une table Excel, ou dans une source de données externe.  
  
3.  Dans la page **Sélectionner le type d’échantillonnage** , indiquez si vous souhaitez créer des jeux de données d’apprentissage et de test par échantillonnage aléatoire, ou créer un nouveau jeu de données par suréchantillonnage.  
  
    > [!NOTE]  
    >  Si vous utilisez une source de données externe, seule l'option d'échantillonnage aléatoire est disponible. Si vous souhaitez utiliser le suréchantillonnage avec des données externes, vous pouvez importer les données dans un classeur Excel en utilisant une connexion de données Excel, puis utiliser l'Assistant Exemples de données.  
  
4.  Définissez les options spécifiques à la méthode d'échantillonnage que vous avez sélectionnée.  
  
    -   Pour l'échantillonnage aléatoire, spécifiez un pourcentage des données d'origine à utiliser pour le test ou le nombre total de lignes à utiliser dans le jeu de données de test.  
  
    -   Pour le suréchantillonnage, sélectionnez la colonne et la valeur à privilégier. Spécifiez ensuite le nombre total de lignes dans le nouveau jeu de données, ainsi que le pourcentage de lignes dans le nouveau jeu de données qui doit inclure la valeur cible.  
  
         La valeur cible pour le suréchantillonnage doit être une valeur discrète ; vous ne pouvez pas suréchantillonner des données numériques continues.  
  
5.  Dans la **page terminer**, acceptez les noms par défaut pour les nouveaux jeux de données ou tapez un nouveau nom.  
  
     L'Assistant crée de nouvelles feuilles de calcul pour chaque jeu de données.  
  
 Dans le Client d'exploration de données pour Excel, la plupart des Assistants proposent également une option permettant de séparer de façon aléatoire les données en jeux d'apprentissage et de test. Toutefois, si vous utilisez les Assistants, vos données demeurent dans la même feuille de calcul (ou autre source de données) et les informations indiquant si une ligne en particulier est un scénario de test ou un cas d'apprentissage sont stockées en interne. En revanche, lorsque vous utilisez l’Assistant **exemples de données** , les données de test et d’apprentissage sont générées dans des feuilles de calcul distinctes pour faciliter leur référence.  
  
## <a name="related-options"></a>Options connexes  
 Au fur et à mesure que vous progressez dans l'Assistant, vous disposez des options suivantes :  
  
|Options|Commentaires|  
|-------------|--------------|  
|Boîte de dialogue Sélectionner les données source (Client d'exploration de données pour Excel)|Sélectionnez une plage Excel ou la table qui contient les données. Si vous souhaitez utiliser des données externes, les données peuvent être relationnelles, mais elles doivent être incluses dans une source de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)]. T|  
|Page Sélectionner le type d'échantillonnage (Client d'exploration de données pour Excel)|Si vous utilisez une source de données externe, vous êtes limité à l'option d'échantillonnage aléatoire. En outre, vous devez spécifier le nombre de lignes à créer dans le jeu de données final, à l’aide de l’option **nombre** de lignes. Vous ne pouvez pas spécifier un pourcentage des données sources.|  
|Page Échantillonnage aléatoire (Client d'exploration de données pour Excel)|Copiez un pourcentage de lignes à partir de la source, ou un nombre spécifique de lignes.|  
|Page Suréchantillonnage (Client d'exploration de données pour Excel)|**État cible**<br /><br /> Sélectionnez une valeur dans la liste sous-représentée dans le jeu de données d'origine. Le suréchantillonnage augmentera la proportion des lignes de données qui incluent cet état.<br /><br /> **Taille d’échantillon**<br /><br /> Sélectionnez le nombre total de lignes à extraire. Cette valeur représente la taille du jeu de données final.|  
  
## <a name="other-sampling-options"></a>Autres options d'échantillonnage  
 Si les options d'échantillonnage de cet Assistant ne répondent pas à vos besoins, vous pouvez utiliser la transformation d'échantillonnage dans SQL Server Integration Services (SSIS) pour échantillonner des lignes de plusieurs sources de données.  
  
 Pour plus d’informations, consultez transformation d' [échantillonnage de lignes](../integration-services/data-flow/transformations/row-sampling-transformation.md) et transformation d' [échantillonnage par pourcentage](../integration-services/data-flow/transformations/percentage-sampling-transformation.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Liste de vérification : préparation pour l'exploration de données](checklist-of-preparation-for-data-mining.md)  
  
  
