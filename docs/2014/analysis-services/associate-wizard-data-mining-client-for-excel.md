---
title: Associer l’Assistant (Client d’exploration de données pour Excel) | Microsoft Docs
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
manager: craigg
ms.openlocfilehash: 15a86cc55e67b2000eabee62d02fa04de4874f59
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66062307"
---
# <a name="associate-wizard-data-mining-client-for-excel"></a>Assistant Association (Client d'exploration de données pour Excel)
  ![Assistant association dans le ruban Exploration de données](media/dmc-associate.gif "associer l’Assistant dans le ruban Exploration de données")  
  
 L'Assistant Association vous permet de créer un modèle d'exploration de données à l'aide de l'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules). Ces modèles d’exploration de données sont particulièrement utiles pour la création de *systèmes de recommandation*.  
  
 L'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules) analyse un dataset comprenant des transactions ou des événements, et trouve les éléments qui apparaissent fréquemment ensemble. Plusieurs milliers de combinaisons sont possibles, mais l'algorithme peut être personnalisé pour obtenir un nombre plus ou moins important, et conserver uniquement les combinaisons les plus probables.  
  
 Appliquez l'analyse d'association à plusieurs problèmes. L'application la plus courante pour cette méthode est l'analyse du panier d'achat, qui détermine les produits individuels souvent achetés ensemble. Vous pouvez ensuite utiliser ces informations pour recommander des produits aux clients en fonction des articles qu'ils ont déjà achetés.  
  
## <a name="using-the-associate-wizard"></a>Utilisation de l'Assistant Association  
  
1.  Dans le **d’exploration de données** ruban, cliquez sur **associer**.  
  
2.  Sur le **sélectionner les données Source** page, choisissez une table ou une plage Excel, puis cliquez sur **suivant**.  
  
     L'exemple de classeur de données montre comment les données sont généralement organisées dans l'onglet Association lorsque, par exemple, vous avez plusieurs produits dans chaque transaction ou plusieurs enregistrements d'achat par client que vous souhaitez analyser.  
  
     Si vous souhaitez utiliser des données externes pour créer un modèle d’association à l’aide de l’Assistant association, vous devez ajouter les données vers Excel tout d’abord, et *aplatir* les données. Pour plus d’informations sur la préparation des données pour la modélisation d’association, consultez [Tables imbriquées &#40;Analysis Services - Exploration de données&#41;](data-mining/nested-tables-analysis-services-data-mining.md), dans la documentation en ligne de SQL Server.  
  
3.  Sur le **Association** page, choisissez la colonne qui identifie la transaction.  
  
     Pour les modèles de panier d'achat, cet identifiant représente l'unité que vous souhaitez modéliser. Voulez-vous analyser les articles que chaque client a achetés au fil du temps, ou voulez-vous analyser le nombre de transactions qui impliquent plusieurs clients ? Dans le premier cas, vous devez choisir l'ID du client, dans le second, vous devez choisir le bon de commande ou l'ID de transaction.  
  
4.  Pour **élément**, sélectionnez la colonne qui contient les éléments pour lesquels vous devez trouver des associations.  
  
     Par exemple, dans le modèle de panier d'achat, vous devez choisir un champ de produit pour analyser quels produits sont souvent achetés ensemble. S'il y a trop de produits distincts pour les corréler efficacement, vous pouvez choisir une catégorie de produit ou une sous-catégorie.  
  
5.  Dans **seuils**, vous pouvez définir les valeurs qui contrôlent ou affectent la sortie du modèle :  
  
    -   **Prise en charge minimale.** Spécifie combien de fois un groupe d'éléments doit apparaître pour qu'il soit considéré comme important. L'algorithme ignorera toutes les combinaisons d'éléments qui ne répondent pas à ce critère. Par exemple, vous pouvez afficher uniquement les jeux d'éléments où les éléments apparaissent ensemble au moins 10 fois au total.  
  
    -   **Probabilité de règle minimum**. Spécifie la valeur de probabilité minimale requise pour enregistrer une règle. L'ensemble du jeu de données est analysé pour trouver toutes les combinaisons, puis la probabilité est calculée. Si le seuil est bas, l'Assistant peut associer des éléments qui ne sont que faiblement corrélés. Si le seuil est trop élevé, certaines associations peuvent être omises car elles ne possèdent pas suffisamment de données de prise en charge.  
  
     En général, la modification de ces valeurs a pour corollaire les effets suivants :  
  
    -   Lorsque vous diminuez la valeur de prise en charge, vous augmentez le nombre de combinaisons qui sont trouvées.  
  
    -   En diminuant la prise en charge maximale, vous éliminez par filtrage les éléments qui se produisent si souvent qu'ils finissent par perdre une grande partie de leur signification.  
  
    -   Lorsque vous diminuez la probabilité d'une règle, vous diminuez les impératifs auxquels une combinaison doit répondre pour être considérée comme importante dans le contexte du jeu de données total.  
  
     **Conseil :** Il est judicieux de créer plusieurs modèles d’exploration de données à l’aide des combinaisons différentes de prise en charge et probabilité. Pour suivre les paramètres utilisés pour chaque modèle, vous pouvez utiliser la **Document modèle** Assistant, disponible dans le Client d’exploration de données pour Excel, puis utilisez le **Detailed** l’option de rapport. Pour plus d’informations, consultez [documentant les modèles d’exploration de données &#40;des compléments d’exploration de données pour Excel&#41;](documenting-mining-models-data-mining-add-ins-for-excel.md).  
  
6.  Si vous le souhaitez, cliquez sur **paramètres** pour modifier les paramètres d’algorithme et personnaliser le comportement du modèle d’exploration de données.  
  
     La boîte de dialogue Paramètres d'algorithme comprend tous les paramètres définis dans l'Assistant, plus quelques paramètres moins couramment utilisés, comme MAXIMUM_SUPPORT. Pour plus d’informations sur l’utilisation de ces paramètres, consultez [l’algorithme Microsoft Association Technical Reference](data-mining/microsoft-association-algorithm-technical-reference.md).  
  
7.  Sur le **Terminer** , tapez un nom unique pour le jeu de données et le modèle.  
  
8.  Dans **Options**, vous définissez la façon dont vous souhaitez utiliser le modèle une fois qu’elle est terminée :  
  
    -   **Parcourir**.  Lorsque le modèle est prêt, l'Assistant ouvre une fenêtre qui affiche les règles, les jeux d'éléments et un diagramme de réseau de dépendances qui décrit les associations.  
  
         Pour plus d’informations sur la façon d’interpréter les données dans la visionneuse de modèle d’association, consultez [exploration d’un modèle de règles d’Association](browsing-an-association-rules-model.md).  
  
    -   **Activer l’extraction**. Sélectionnez cette option pour pouvoir accéder aux données sous-jacentes via le modèle.  
  
         L'extraction est utile, par exemple, si vous souhaitez cliquer sur un jeu d'éléments spécifique et voir les données sources.  
  
    -   **Utiliser le modèle temporaire**. Sélectionnez cette option si vous ne souhaitez pas le modèle enregistré sur le serveur. Lorsque vous fermez Excel, les modèles temporaires sont supprimés.  
  
9. L'Assistant analyse toutes les combinaisons possibles et crée un rapport qui contient des jeux d'éléments et des règles.  
  
## <a name="more-about-association-models"></a>En savoir plus sur les modèles d'association  
 L'algorithme MAR ([!INCLUDE[msCoName](../includes/msconame-md.md)] Association Rules) examine les données d'apprentissage pour trouver les éléments qui apparaissent ensemble dans une transaction. Chaque groupe d’éléments constitue un *jeu d’éléments*. L'algorithme compte ensuite le nombre de fois où chaque jeu d'éléments apparaît et calcule l'importance relative de chaque jeu d'éléments dans toutes les transactions.  
  
 L'algorithme utilise ces informations sur les jeux d'éléments pour générer des règles qui peuvent être utilisées pour prédire des associations ou faire des recommandations. Par exemple, une règle peut énoncer « si l'utilisateur a acheté un livre de l'auteur 1 et un livre de l'auteur 2, il est probable qu'il achètera aussi un livre de l'auteur 3 ». Une probabilité est attribuée à chaque recommandation, en fonction de la force des associations.  
  
### <a name="requirements"></a>Configuration requise  
 Pour pouvoir utiliser l'Assistant Association, vous devez être connecté à une base de données [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)].  
  
 Vos données sources doivent être organisées sous forme de table des transactions. Les données sources doivent contenir une colonne incluant l'identificateur de transaction. Cette colonne identifie chaque groupe d'éléments. Cette colonne Transaction doit être dans une relation un-à-plusieurs avec une seconde colonne, la colonne Identificateur d'élément, qui stocke les noms ou les numéros d'ID des différents éléments du groupe.  
  
 D'un point de vue conceptuel, ceci peut être facile à comprendre si vous repensez à l'exemple du caddie. Si un ID est affecté au caddie, l'ID du caddie fait office d'identificateur de la transaction. Chaque article du caddie, comme les pommes de terre ou le lait, est membre de cette transaction. L'algorithme Association peut effectuer le suivi des éléments entre plusieurs transactions, par exemple pour déterminer combien de fois pommes de terre et lait apparaissent dans une même transaction.  
  
 Vos données sources doivent être triées en fonction de la colonne d'identificateur de transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Création d’un modèle d’exploration de données](creating-a-data-mining-model.md)   
 [Exploration d’un modèle de règles d’Association](browsing-an-association-rules-model.md)   
 [Analyse de panier d’achat &#40;outils d’analyse de Table pour Excel&#41;](shopping-basket-analysis-table-analysistools-for-excel.md)   
 [Procédure pas à pas de dépendance réseau diagramme &#40;compléments d’exploration de données&#41;](dependency-network-diagram-walkthrough-data-mining-add-ins.md)  
  
  
