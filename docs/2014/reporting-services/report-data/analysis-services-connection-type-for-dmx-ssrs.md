---
title: Type de connexion Analysis Services pour DMX (SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/07/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: reporting-services-native
ms.topic: conceptual
helpviewer_keywords:
- parameters [Reporting Services], DMX
- Data Mining Prediction [Reporting Services]
- query view [Reporting Services]
- DMX [Reporting Services]
- design view [Reporting Services]
- data mining [Reporting Services]
- passing parameters [Reporting Services]
ms.assetid: 2de825e9-6d8a-4128-add0-da15dc6cea3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 53a22e87ead90694dea0511be206c50f52663102
ms.sourcegitcommit: f40fa47619512a9a9c3e3258fda3242c76c008e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2019
ms.locfileid: "66107505"
---
# <a name="analysis-services-connection-type-for-dmx-ssrs"></a>Type de connexion Analysis Services pour DMX (SSRS)
  Quand vous créez un dataset à l’aide d’une source de données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] , le Concepteur de rapports affiche le Concepteur de requêtes MDX (Multidimensional Expression) s’il détecte un cube valide. Si aucun cube n'est détecté, mais qu'un modèle d'exploration de données est disponible, le Concepteur de rapports affiche le Concepteur de requêtes DMX (Data Mining Extensions). Pour basculer entre les concepteurs MDX et DMX, cliquez sur le bouton **Type de commande DMX** (![Basculer vers la vue langage de requête DMX](../media/rsqdicon-commandtypedmx.gif "Basculer vers la vue langage de requête DMX")) dans la barre d’outils. Utilisez le Concepteur de requêtes DMX pour créer de manière interactive une requête DMX à l'aide d'éléments graphiques. Pour utiliser le Concepteur de requêtes DMX, la source de données que vous spécifiez doit déjà avoir un modèle d'exploration de données qui fournit les données. Les résultats de requête sont convertis en un jeu de lignes à deux dimensions qui sera utilisé dans le rapport.  
  
> [!NOTE]  
>  Vous devez former le modèle avant de concevoir le rapport. Pour plus d’informations, consultez [Solutions d’exploration de données](../../analysis-services/data-mining/data-mining-solutions.md).  
  
## <a name="design-mode"></a>Mode Création  
 Le Concepteur de requêtes DMX s'ouvre en mode Création. Le mode Création comprend une zone de conception graphique permettant de sélectionner un modèle d'exploration de données et une table d'entrée, ainsi qu'une grille utilisée pour spécifier la requête de prédiction. Il existe deux autres modes dans le Concepteur de requêtes DMX : Mode de requête et le mode de résultat. En mode Requête, la grille du mode Création est remplacée par un volet Requête, qui vous permet de taper des requêtes DMX. En mode Résultat, le jeu de résultats retourné par la requête apparaît dans une grille de données.  
  
 Pour changer de mode dans le Concepteur de requêtes DMX, cliquez avec le bouton droit dans la zone de conception, puis sélectionnez **Création** **Requête**ou **Résultat**. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes DMX Analysis Services](analysis-services-dmx-query-designer-user-interface.md) et [Récupérer des données d’un modèle d’exploration de données &#40;DMX&#41; &#40;SSRS&#41;](retrieve-data-from-a-data-mining-model-dmx-ssrs.md).  
  
## <a name="designing-a-prediction-query"></a>Conception d'une requête de prédiction  
 Le volet de conception de requête du mode Création contient deux fenêtres : **Modèle d’exploration de données** et **sélectionner la Table d’entrée**. La fenêtre **Modèle d’exploration de données** vous permet de sélectionner le modèle d’exploration de données à utiliser dans la requête. La fenêtre **Sélectionner une ou plusieurs tables d’entrée** vous permet de sélectionner la table sur laquelle baser les prévisions. Si vous souhaitez utiliser une requête singleton au lieu d’une table d’entrée, cliquez avec le bouton droit dans le volet Conception de requête, puis sélectionnez **Requête singleton**. La fenêtre **Sélectionner une ou plusieurs tables d’entrée** est remplacée par une fenêtre **Entrée de requête singleton** .  
  
 En mode Création, faites glisser les champs des fenêtres **Modèle d’exploration de données** et **Sélectionner une ou plusieurs tables d’entrée** vers la colonne **Champ** du volet Grille. Vous pouvez également remplir les colonnes restantes pour spécifier un alias, afficher le champ dans les résultats, regrouper des champs et spécifier un opérateur pour restreindre la valeur de champ à un critère ou argument donné. Si vous utilisez le mode Requête, générez la requête DMX en faisant glisser des champs vers le volet Requête.  
  
## <a name="using-parameters"></a>Utilisation des paramètres  
 Vous pouvez transmettre des paramètres de rapport à un paramètre de requête DMX. Pour ce faire, vous devez ajouter un paramètre à la requête DMX, définir les paramètres de requête dans la boîte de dialogue **Paramètres de la requête** , puis modifier les paramètres de rapport correspondants. Pour définir un paramètre de requête, cliquez sur le bouton **Paramètres de la requête** (![Icône de la boîte de dialogue Paramètres de la requête](../../analysis-services/media/iconqueryparameter.gif "Icône de la boîte de dialogue Paramètres de la requête")) dans la barre d’outils. Pour obtenir des instructions sur la définition des paramètres dans une requête DMX, consultez [Définir des paramètres dans le Concepteur de requêtes MDX pour Analysis Services &#40;Générateur de rapports et SSRS&#41;](define-parameters-in-the-mdx-query-designer-for-analysis-services.md).  
  
 Pour plus d’informations sur la façon de gérer la relation entre les paramètres de rapport et les paramètres de requête, consultez [Associer un paramètre de requête à un paramètre de rapport &#40;Générateur de rapports et SSRS&#41;](associate-a-query-parameter-with-a-report-parameter-report-builder-and-ssrs.md). Pour plus d’informations sur les paramètres, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](../report-design/report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Solutions d’exploration de données](../../analysis-services/data-mining/data-mining-solutions.md)   
 [Interroger des outils de conception dans le rapport concepteur SQL Server Data Tools &#40;SSRS&#41;](query-design-tools-ssrs.md)   
 [Connexions de données, sources de données et chaînes de connexion dans Reporting Services](../data-connections-data-sources-and-connection-strings-in-reporting-services.md)  
  
  
