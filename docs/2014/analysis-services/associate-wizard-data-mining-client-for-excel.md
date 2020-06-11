---
title: Assistant Association (client d’exploration de données pour Excel) | Microsoft Docs
ms.custom: ''
ms.date: 12/29/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: analysis-services
ms.topic: conceptual
helpviewer_keywords:
- nested tables, in association models
- association [data mining]
ms.assetid: 4db6462f-93c7-443f-8ff7-39474dc7029e
author: minewiskan
ms.author: owend
ms.openlocfilehash: 52542ac1b15b59ecebca4ea26ba530298157ed50
ms.sourcegitcommit: 2f166e139f637d6edfb5731510d632a13205eb25
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84527941"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a>Assistant Association (Client d'exploration de données pour Excel)
  ![Assistant Association sur le ruban Exploration de données](media/dmc-associate.gif "Assistant Association sur le ruban Exploration de données")  
  
 L'Assistant Association vous permet de créer un modèle d'exploration de données à l'aide de l'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules). Ces modèles d’exploration de données sont particulièrement utiles pour créer des *systèmes de recommandation*.  
  
 L'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules) analyse un dataset comprenant des transactions ou des événements, et trouve les éléments qui apparaissent fréquemment ensemble. Plusieurs milliers de combinaisons sont possibles, mais l'algorithme peut être personnalisé pour obtenir un nombre plus ou moins important, et conserver uniquement les combinaisons les plus probables.  
  
 Appliquez l'analyse d'association à plusieurs problèmes. L'application la plus courante pour cette méthode est l'analyse du panier d'achat, qui détermine les produits individuels souvent achetés ensemble. Vous pouvez ensuite utiliser ces informations pour recommander des produits aux clients en fonction des articles qu'ils ont déjà achetés.  
  
## <a name="using-the-associate-wizard"></a>Utilisation de l'Assistant Association  
  
1.  Dans le ruban **exploration de données** , cliquez sur **associer**.  
  
2.  Dans la page **Sélectionner les données sources** , choisissez un tableau ou une plage de données Excel, puis cliquez sur **suivant**.  
  
     L'exemple de classeur de données montre comment les données sont généralement organisées dans l'onglet Association lorsque, par exemple, vous avez plusieurs produits dans chaque transaction ou plusieurs enregistrements d'achat par client que vous souhaitez analyser.  
  
     Si vous souhaitez utiliser des données externes pour créer un modèle d’association à l’aide de l’Assistant Association, vous devez d’abord ajouter les données à Excel et *aplatir* les données. Pour plus d’informations sur la préparation des données pour la modélisation d’association, consultez [tables imbriquées &#40;Analysis Services-exploration de données&#41;](data-mining/nested-tables-analysis-services-data-mining.md), dans documentation en ligne de SQL Server.  
  
3.  Dans la page **Association** , choisissez la colonne qui identifie la transaction.  
  
     Pour les modèles de panier d'achat, cet identifiant représente l'unité que vous souhaitez modéliser. Voulez-vous analyser les articles que chaque client a achetés au fil du temps, ou voulez-vous analyser le nombre de transactions qui impliquent plusieurs clients ? Dans le premier cas, vous devez choisir l'ID du client, dans le second, vous devez choisir le bon de commande ou l'ID de transaction.  
  
4.  Pour **élément**, sélectionnez la colonne qui contient les éléments parmi lesquels vous devez rechercher des associations.  
  
     Par exemple, dans le modèle de panier d'achat, vous devez choisir un champ de produit pour analyser quels produits sont souvent achetés ensemble. S'il y a trop de produits distincts pour les corréler efficacement, vous pouvez choisir une catégorie de produit ou une sous-catégorie.  
  
5.  Dans **seuils**, vous pouvez définir des valeurs qui contrôlent ou affectent la sortie du modèle :  
  
    -   **Prise en charge minimale.** Spécifie combien de fois un groupe d'éléments doit apparaître pour qu'il soit considéré comme important. L'algorithme ignorera toutes les combinaisons d'éléments qui ne répondent pas à ce critère. Par exemple, vous pouvez afficher uniquement les jeux d'éléments où les éléments apparaissent ensemble au moins 10 fois au total.  
  
    -   **Probabilité de règle minimale**. Spécifie la valeur de probabilité minimale requise pour enregistrer une règle. L'ensemble du jeu de données est analysé pour trouver toutes les combinaisons, puis la probabilité est calculée. Si le seuil est bas, l'Assistant peut associer des éléments qui ne sont que faiblement corrélés. Si le seuil est trop élevé, certaines associations peuvent être omises car elles ne possèdent pas suffisamment de données de prise en charge.  
  
     En général, la modification de ces valeurs a pour corollaire les effets suivants :  
  
    -   Lorsque vous diminuez la valeur de prise en charge, vous augmentez le nombre de combinaisons qui sont trouvées.  
  
    -   En diminuant la prise en charge maximale, vous éliminez par filtrage les éléments qui se produisent si souvent qu'ils finissent par perdre une grande partie de leur signification.  
  
    -   Lorsque vous diminuez la probabilité d'une règle, vous diminuez les impératifs auxquels une combinaison doit répondre pour être considérée comme importante dans le contexte du jeu de données total.  
  
     **Conseil :** Il est judicieux de créer plusieurs modèles d’exploration de données à l’aide de différentes combinaisons de prise en charge et de probabilité. Pour suivre les paramètres que vous avez utilisés pour chaque modèle, vous pouvez utiliser l’Assistant **modèle de document** , disponible dans le client d’exploration de données pour Excel, et utiliser l’option rapport **détaillé** . Pour plus d’informations, consultez [documentation des modèles d’exploration de données &#40;compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).  
  
6.  Si vous le souhaitez, cliquez sur **paramètres** pour modifier les paramètres d’algorithme et personnaliser le comportement du modèle d’exploration de données.  
  
     La boîte de dialogue Paramètres d'algorithme comprend tous les paramètres définis dans l'Assistant, plus quelques paramètres moins couramment utilisés, comme MAXIMUM_SUPPORT. Pour plus d’informations sur l’utilisation de ces paramètres, consultez informations techniques de référence sur l' [algorithme Microsoft Association](data-mining/microsoft-association-algorithm-technical-reference.md).  
  
7.  Dans la page **Terminer** , tapez un nom unique pour le jeu de données et le modèle.  
  
8.  Dans **options**, vous définissez la manière dont vous souhaitez utiliser le modèle une fois qu’il est terminé :  
  
    -   **Parcourir**.  Lorsque le modèle est prêt, l'Assistant ouvre une fenêtre qui affiche les règles, les jeux d'éléments et un diagramme de réseau de dépendances qui décrit les associations.  
  
         Pour plus d’informations sur la façon d’interpréter les données dans la visionneuse de modèle d’association, consultez [exploration d’un modèle de règles d’association](browsing-an-association-rules-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour pouvoir accéder aux données sous-jacentes via le modèle.  
  
         L'extraction est utile, par exemple, si vous souhaitez cliquer sur un jeu d'éléments spécifique et voir les données sources.  
  
    -   **Utilisez le modèle temporaire**. Sélectionnez cette option si vous ne souhaitez pas enregistrer le modèle sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
9. L'Assistant analyse toutes les combinaisons possibles et crée un rapport qui contient des jeux d'éléments et des règles.  
  
## <a name="more-about-association-models"></a>En savoir plus sur les modèles d'association  
 L'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules) examine les données d'apprentissage pour trouver les éléments qui apparaissent ensemble dans une transaction. Chaque groupe d’éléments constitue un *jeu d’éléments*. L'algorithme compte ensuite le nombre de fois où chaque jeu d'éléments apparaît et calcule l'importance relative de chaque jeu d'éléments dans toutes les transactions.  
  
 L'algorithme utilise ces informations sur les jeux d'éléments pour générer des règles qui peuvent être utilisées pour prédire des associations ou faire des recommandations. Par exemple, une règle peut énoncer « si l'utilisateur a acheté un livre de l'auteur 1 et un livre de l'auteur 2, il est probable qu'il achètera aussi un livre de l'auteur 3 ». Une probabilité est attribuée à chaque recommandation, en fonction de la force des associations.  
  
### <a name="requirements"></a>Spécifications  
 Pour pouvoir utiliser l'Assistant Association, vous devez être connecté à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Vos données sources doivent être organisées sous forme de table des transactions. Les données sources doivent contenir une colonne incluant l'identificateur de transaction. Cette colonne identifie chaque groupe d'éléments. Cette colonne Transaction doit être dans une relation un-à-plusieurs avec une seconde colonne, la colonne Identificateur d'élément, qui stocke les noms ou les numéros d'ID des différents éléments du groupe.  
  
 D'un point de vue conceptuel, ceci peut être facile à comprendre si vous repensez à l'exemple du caddie. Si un ID est affecté au caddie, l'ID du caddie fait office d'identificateur de la transaction. Chaque article du caddie, comme les pommes de terre ou le lait, est membre de cette transaction. L'algorithme Association peut effectuer le suivi des éléments entre plusieurs transactions, par exemple pour déterminer combien de fois pommes de terre et lait apparaissent dans une même transaction.  
  
 Vos données sources doivent être triées en fonction de la colonne d'identificateur de transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Exploration d’un modèle de règles d’association](browsing-an-association-rules-model.md)   
 [Analyse du panier d’achat &#40;table outils pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)   
 [Procédure pas à pas de diagramme de réseau de dépendances &#40;compléments d’exploration de données&#41;](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  
