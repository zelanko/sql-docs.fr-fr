---
title: Volet (vue prévision de modèle d’exploration de données) de conception | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.dm.miningmodeleditor.prediction.design.f1
ms.assetid: 17f24c8d-43cd-4f4d-83b3-a41ee8fbe8e8
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 28774dc49ba3052ee01d197570f3de87f7363cf2
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48189761"
---
# <a name="design-pane-mining-model-prediction-view"></a>Volet Conception (vue Prévision de modèle d'exploration de données)
  Le volet **Conception** contient le Générateur de requêtes de prédiction qui peut servir à créer des prédictions d’exploration de données. Vous pouvez concevoir des requêtes de prédiction qui utilisent des tables de données d'entrée d'une vue de source de données, pour générer des prédictions en bloc, ou vous pouvez créer des requêtes singleton de prédiction qui vous permettent de fournir des valeurs individuelles.  
  
 Pour exécuter la requête et afficher les résultats, basculer vers l'affichage du résultat de la requête.  
  
 La vue **Requête** affiche la requête DMX (Data Mining Extensions) créée par le Générateur de requêtes de prévision. Si vous connaissez DMX, vous pouvez personnaliser cette requête.  
  
> [!NOTE]  
>  Si vous apportez des modifications manuelles à la requête, vous perdez les modifications lorsque vous repassez en mode Conception. Pour enregistrer la requête DMX, vous pouvez copier celle-ci vers le Presse-papiers Windows puis la coller dans un fichier texte.  
  
 **Pour plus d’informations :**[Requêtes d’exploration de données](data-mining/data-mining-queries.md)  
  
## <a name="options"></a>Options  
 **Basculez vers l’affichage des résultats de requête**  
 Sélectionnez cette option pour basculer entre les volets **Conception**, **Requête**et **Résultat** . Lorsque vous basculez vers le volet **Résultat** , la requête est exécutée.  
  
 **Enregistrer le résultat de requête**  
 Ouvre la boîte de dialogue **Enregistrer le résultat de la requête d’exploration de données** .  
  
 **Requête singleton**  
 Permet la création d'une requête singleton, dans laquelle vous pouvez fournir directement des valeurs pour la requête au lieu d'une table comme source des données connues. Le tableau **Sélectionner une ou plusieurs tables d’entrée** est remplacé par un tableau **Entrée de requête singleton** .  
  
 **Actualiser les résultats de requête**  
 Traite une nouvelle fois la requête de prévision. Cette option est activée uniquement dans le volet **Résultat** .  
  
 **Modèle d'exploration de données**  
 Choisissez le modèle d'exploration de données sur lequel vous souhaitez baser vos prévisions.  
  
 **Sélectionner un modèle**  
 Ouvre la boîte de dialogue **Sélectionnez un modèle d’exploration de données** .  
  
 **Sélectionnez une ou plusieurs tables d’entrée**  
 Affiche les tables d'entrée sélectionnées qui contiennent les données connues sur lesquelles baser les prévisions.  
  
 **Supprimer la Table**  
 Supprime la table sélectionnée. Ce bouton est désactivé si aucune table n'a été sélectionnée ou si elle n'existe pas.  
  
 **Sélectionnez la Table de cas**  
 Ouvre la boîte de dialogue **Sélectionner une table** . Ce bouton s'affiche uniquement si aucune table de cas n'a été sélectionnée.  
  
 **Sélectionner la Table imbriquée**  
 Ouvre la boîte de dialogue **Sélectionner une table** . Ce bouton s'affiche uniquement si une table de cas a été sélectionnée. Si la structure d'exploration de données associée ne contient pas de table imbriquée, ce bouton est désactivé.  
  
 **Modifier la jointure**  
 Ouvre la boîte de dialogue **Spécifier la jointure imbriquée** . Ce bouton est activé uniquement si la table imbriquée est sélectionnée.  
  
 **Entrée de requête singleton**  
 Cette option est activée quand vous sélectionnez le bouton **Requête singleton** . Elle contient les colonnes suivantes :  
  
|Valeur|Description|  
|-----------|-----------------|  
|**Colonne du modèle d’exploration de données**|Affiche la liste des colonnes du modèle d’exploration de données sélectionné dans la table **Modèle d’exploration de données** .|  
|**Valeur**|Sélectionnez une valeur dans la liste qui contient tous les états possibles de la colonne du modèle d'exploration de données sélectionné.<br /><br /> Si la colonne est une colonne de table imbriquée, la boîte de dialogue **Entrée de la table imbriquée** s’ouvre quand vous cliquez dans la cellule de la valeur.|  
  
 **Source**  
 Sélectionnez la source qui contient le champ que vous allez utiliser pour la colonne. Vous pouvez utiliser le modèle d’exploration de données sélectionné dans la table **Modèle d’exploration de données** , la ou les tables d’entrée sélectionnées dans la table **Sélectionner une ou plusieurs tables d’entrée** , une fonction de prédiction ou une expression personnalisée.  
  
 Les colonnes des tables contenant le modèle d'exploration de données et des tables d'entrée peuvent être glissées et déplacées sur la cellule.  
  
 **Field**  
 Sélectionnez une colonne dans la liste des colonnes dérivées de la table source. Si vous avez sélectionné **Fonction de prédiction** dans **Source**, elle contient la fonction de prédiction disponible pour le modèle d’exploration de données sélectionné.  
  
 **Grouper**  
 Utilisez cette option avec la colonne **et/ou** pour regrouper les expressions. Par exemple, `(expr1 Or expr2) And expr3`.  
  
 **et/ou**  
 Utilisez cette option pour créer une requête logique. Par exemple, `(expr1 Or expr2) And expr3`.  
  
 **Critères/Argument**  
 Spécifiez une condition ou une expression utilisateur qui s'applique à la colonne. Les colonnes des tables contenant le modèle d'exploration de données et des tables d'entrée peuvent être glissées et déplacées sur la cellule.  
  
## <a name="see-also"></a>Voir aussi  
 [Data Mining Extensions &#40;DMX&#41; référence des instructions](/sql/dmx/data-mining-extensions-dmx-statements)   
 [Interfaces de requête d’exploration de données](data-mining/data-mining-query-tools.md)   
 [Générateur de requêtes de prédiction &#40;exploration de données&#41;](prediction-query-builder-data-mining.md)  
  
  
