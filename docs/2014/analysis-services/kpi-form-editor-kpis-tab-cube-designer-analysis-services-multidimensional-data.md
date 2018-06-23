---
title: Éditeur de formulaire d’indicateur de performance clé (onglet des indicateurs de performance clés, Concepteur de Cube) (Analysis Services - données multidimensionnelles) | Documents Microsoft
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
- sql12.asvs.cubeeditor.kpidefinitionpane.f1
ms.assetid: 45c6453a-bbe2-4ca5-836e-c7ef11cfcb65
caps.latest.revision: 23
author: Minewiskan
ms.author: owend
manager: mblythe
ms.openlocfilehash: af159d0cdc724af8f0b7e768146527588b4e16fc
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042135"
---
# <a name="kpi-form-editor-kpis-tab-cube-designer-analysis-services---multidimensional-data"></a>Éditeur de formulaire d'indicateur de performance clé (onglet Indicateurs de performance clés, Concepteur de cube) (Analysis Services - Données multidimensionnelles)
  Utilisez le volet **Éditeur de formulaire d’indicateur de performance clé** de l’onglet **Indicateurs de performance clés** dans le Concepteur de cube pour créer ou modifier l’indicateur de performance clé sélectionné.  
  
> [!NOTE]  
>  Ce volet s'affiche uniquement en mode Formulaire.  
  
## <a name="options"></a>Options  
 **Nom**  
 Tapez le nom de l'indicateur de performance clé.  
  
 **Groupe de mesures associé**  
 Sélectionnez le groupe de mesures associé à l'indicateur de performance clé. L'application cliente peut utiliser cette information pour déterminer les dimensions disponibles lorsque l'utilisateur consulte les indicateurs de performance clé.  
  
 **Expression de valeur**  
 Développez pour afficher ou modifier l'expression MDX (Multidimensional Expressions) de la valeur de l'indicateur de performance clé.  
  
 Tapez l'expression MDX qui retourne la valeur de l'indicateur.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 **Expression d’objectif**  
 Développez pour afficher ou modifier l'expression MDX de la valeur d'objectif de l'indicateur de performance clé.  
  
 Tapez l'expression MDX qui retourne la valeur d'objectif de l'indicateur de performance clé lorsque ce dernier est exécuté.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 **État**  
 Développez pour afficher les options **Graphique d’état** et **Expression d’état** .  
  
 **Graphique d’état**  
 Sélectionnez le graphique que doit utiliser l'application cliente pour représenter la valeur d'état dans un graphique.  
  
> [!NOTE]  
>  L'application cliente peut prendre en charge le graphique sélectionné ou le remplacer par un autre graphique.  
  
 **Expression d’état**  
 Tapez l'expression MDX qui retourne la valeur d'état de l'indicateur de performance clé lorsque ce dernier est exécuté.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 Il est recommandé que cette expression retourne une valeur décimale comprise entre –1 et 1. Une valeur inférieure représente une situation négative alors qu'une valeur supérieure représente une situation positive.  
  
> [!NOTE]  
>  Il est possible d'utiliser des valeurs inférieures à –1 et supérieures à 1, mais elles peuvent ne pas être interprétées correctement par les applications clientes tierces.  
  
 **Tendance**  
 Développez pour afficher les options **Graphique de tendance** et **Expression de tendance** .  
  
 **Graphique de tendance**  
 Sélectionnez le graphique que doit utiliser l'application cliente pour représenter la valeur de tendance dans un graphique.  
  
> [!NOTE]  
>  L'application cliente peut prendre en charge le graphique sélectionné ou le remplacer par un autre graphique.  
  
 **Expression de tendance**  
 Tapez l'expression MDX qui retourne la valeur de tendance de l'indicateur de performance clé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 L'expression de tendance peut être basée sur un critère temps qui a une signification dans un contexte d'entreprise. Il est recommandé que cette expression retourne une valeur décimale comprise entre –1 et 1. Une valeur inférieure représente une tendance négative dans le temps alors qu'une valeur supérieure représente une tendance positive.  
  
> [!NOTE]  
>  Il est possible d'utiliser des valeurs inférieures à –1 et supérieures à 1, mais elles peuvent ne pas être interprétées correctement par les applications clientes tierces.  
  
 **Propriétés supplémentaires**  
 Développez pour afficher les options **Afficher le dossier**, **Indicateur de performance clé parent**, **Membre à l’heure actuelle**, **Poids**et **Description** .  
  
 **Dossier d’affichage**  
 Tapez la catégorisation de l'indicateur de performance clé que doit utiliser l'application cliente pour l'affichage.  
  
 Utilisez une barre oblique inverse (\\) pour séparer les noms de dossiers dans le dossier d’affichage, et un point-virgule (;) pour séparer plusieurs dossiers d’affichage. Par exemple, tapez `Category\Goal\Scientific;Category\Goal\Metric`.  
  
 **KPI parent**  
 Sélectionnez un indicateur de performance clé existant pour catégoriser l'indicateur de performance clé que doit utiliser l'application cliente.  
  
> [!NOTE]  
>  Si cette option est affectée d’un indicateur de performance clé existant, **Afficher le dossier** est ignoré.  
  
 **Membre de temps actuel**  
 Tapez l'expression MDX qui retourne le membre qui identifie le contexte temporel de l'indicateur de performance clé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
> [!IMPORTANT]  
>  L’expression MDX doit retourner le nom unique d’un membre dans une dimension de temps associée au groupe de mesures défini dans **Groupe de mesures associé**.  
  
 **Weight**  
 Développez pour afficher ou modifier l'expression MDX du facteur de poids de l'indicateur de performance clé.  
  
 Faites glisser les éléments sélectionnés du volet **Outils de calcul** dans cette option pour inclure la syntaxe MDX de l'élément sélectionné.  
  
 **Description**  
 Tapez la description facultative de l'indicateur de performance clé.  
  
## <a name="see-also"></a>Voir aussi  
 [Indicateurs de performance clés &#40;Concepteur de Cube&#41; &#40;Analysis Services - données multidimensionnelles&#41;](kpis-cube-designer-analysis-services-multidimensional-data.md)  
  
  