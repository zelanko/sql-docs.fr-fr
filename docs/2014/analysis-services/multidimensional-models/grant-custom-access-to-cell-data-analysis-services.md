---
title: Octroyer un accès personnalisé aux données des cellules (Analysis Services) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
f1_keywords:
- sql12.asvs.roledesignerdialog.celldata.f1
helpviewer_keywords:
- user access rights [Analysis Services], cell data
- permissions [Analysis Services], cells
- read contingent permissions
- read permissions
- cells [Analysis Services]
- custom cell data access [Analysis Services]
ms.assetid: 3b13a4ae-f3df-4523-bd30-b3fdf71e95cf
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: fc9d003fc4c1f3b3cd32e8f23fe635d56e48555e
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52510902"
---
# <a name="grant-custom-access-to-cell-data-analysis-services"></a>Octroyer un accès personnalisé à des données de cellule (Analysis Services)
  La sécurité de cellule permet d'accorder ou de refuser l'accès à des données de mesure dans un cube. L'illustration ci-dessous montre une combinaison de mesures autorisées et refusées dans un tableau croisé dynamique, quand vous êtes connecté en tant qu'utilisateur dont le rôle autorise uniquement l'accès à certaines mesures. Dans cet exemple, **Reseller Sales Amount** et **Reseller Total Product Cost** sont les seules mesures accessibles avec ce rôle. L'accès à toutes les autres mesures est refusé de manière implicite (les étapes nécessaires pour obtenir ce résultat sont fournies plus bas dans la section suivante, intitulée Autoriser l'accès à des mesures spécifiques).  
  
 ![Tableau croisé dynamique montrant autorisés et refusés des cellules](../media/ssas-permscellsallowed.png "tableau croisé dynamique montrant autorisés et refusés des cellules")  
  
 Les autorisations de cellules s'appliquent aux données qui figurent à l'intérieur des cellules, et non à leurs métadonnées. Notez que la cellule est encore visible dans les résultats d'une requête et contient la valeur `#N/A` au lieu de sa valeur réelle. Le `#N/A` valeur apparaît dans la cellule, sauf si l’application cliente traduise la valeur ou une autre valeur est spécifiée en définissant la propriété Secured Cell Value dans la chaîne de connexion.  
  
 Pour masquer complètement la cellule, vous devez limiter les dimensions de membres, les attributs de dimension et les membres d’attribut de dimension-qui sont visibles. Pour plus d’informations, consultez [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md).  
  
 En tant qu'administrateur, vous pouvez spécifier si les membres d'un rôle disposent d'autorisations de lecture, de lecture du contingent ou de lecture/écriture sur les cellules d'un cube. Définir des autorisations sur une cellule est le niveau de sécurité le plus bas autorisé. Avant de commencer à appliquer des autorisations à ce niveau, vous devez par conséquent tenir compte des facteurs suivants :  
  
-   La sécurité au niveau de la cellule ne peut pas étendre des droits qui ont été restreints à un niveau supérieur. Exemple : si un rôle refuse l’accès à des données de dimension, la sécurité au niveau de la cellule ne peut pas remplacer le jeu refusé. Un autre exemple : imaginez un rôle avec `Read` autorisation sur un cube et **en lecture/écriture** autorisation sur une cellule de l’autorisation de données de cellule ne sera pas **en lecture/écriture**; il sera `Read`.  
  
-   Les autorisations personnalisées doivent souvent être coordonnées entre les membres de dimension et les cellules dans le même rôle. Par exemple, supposez que vous souhaitez refuser l'accès à plusieurs mesures liées à des remises pour différentes combinaisons de revendeurs. En considérant **Resellers** comme données de dimension et **Discount Amount** comme mesure, vous devrez combiner dans le même rôle les autorisations à la fois sur la mesure (à l’aide des instructions fournies dans cette rubrique) et sur les membres de dimension. Pour plus d’informations sur la définition des autorisations de dimension, consultez [Grant custom access to dimension data &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md) .  
  
 La sécurité au niveau de la cellule est spécifiée via des expressions MDX. Une cellule étant un tuple (autrement dit, un point d'intersection parmi plusieurs dimensions et mesures potentielles), il est nécessaire d'utiliser MDX pour identifier des cellules spécifiques.  
  
## <a name="allow-access-to-specific-measures"></a>Autoriser l'accès à des mesures spécifiques  
 Vous pouvez utiliser la sécurité de cellule pour choisir de manière explicite les mesures qui sont disponibles. Une fois que vous avez identifié de manière spécifique les membres qui sont autorisés, toutes les autres mesures deviennent indisponibles. Il s'agit peut-être du scénario le plus simple à implémenter via un script MDX, comme l'illustrent les étapes ci-dessous.  
  
1.  Dans [!INCLUDE[ssManStudioFull](../../includes/ssmanstudiofull-md.md)] , connectez-vous à l’instance de [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], sélectionnez une base de données, ouvrez le dossier **Rôles** , puis cliquez sur un rôle de base de données (ou créez-en un). L'appartenance doit déjà être spécifiée et le rôle doit avoir un accès `Read` au cube. Pour plus d’informations, consultez [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md) .  
  
2.  Dans **Données des cellules**, vérifiez la sélection du cube pour être sûr d'avoir choisi le bon cube, puis sélectionnez **Activer les autorisations de lecture**.  
  
     Si vous cochez uniquement cette case, sans fournir d'expression MDX, l'effet est le même que si vous refusiez l'accès à toutes les cellules du cube. Cela est dû au fait que l'ensemble autorisé par défaut est un ensemble vide chaque fois qu' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] résout un sous-ensemble de cellules de cube.  
  
3.  Entrez l'expression MDX suivante.  
  
    ```  
    (Measures.CurrentMember IS [Measures].[Reseller Sales Amount]) OR (Measures.CurrentMember IS [Measures].[Reseller Total Product Cost])  
    ```  
  
     Cette expression identifie de manière explicite les mesures que les utilisateurs peuvent voir. Aucune autre mesure ne sera accessible aux utilisateurs qui se connectent avec ce rôle. Notez que [CurrentMember &#40;MDX&#41;](/sql/mdx/current-mdx) définit le contexte et est suivi de la mesure autorisée. L'effet de cette expression est le suivant : si le membre actif comprend le **Reseller Sales Amount** ou le **Reseller Total Product Cost**, la valeur est affichée. Sinon, l'accès est refusé. L'expression comporte plusieurs parties, chacune placée entre parenthèses. L'opérateur `OR` sert à spécifier plusieurs mesures.  
  
## <a name="deny-access-to-specific-measures"></a>Refuser l'accès à des mesures spécifiques  
 L’expression MDX suivante, également spécifiée dans **Créer un rôle** | **Données des cellules** | **Autoriser la lecture du contenu du cube**, a l’effet contraire, en rendant certaines mesures non disponibles. Dans cet exemple, **Discount Amount** et **Discount Percentage** deviennent indisponibles à l’aide du `NOT` et `AND` opérateurs. Toutes les autres mesures sont visibles par les utilisateurs qui se connectent avec ce rôle.  
  
```  
(NOT Measures.CurrentMember IS [Measures].[Discount Amount]) AND (NOT Measures.CurrentMember IS [Measures].[Discount Percentage])  
```  
  
 Dans Excel, la sécurité de cellule est évidente dans l'illustration suivante :  
  
 ![Colonnes Excel montrant les cellules comme indisponibles](../media/ssas-permscellshidemeasure.png "colonnes Excel montrant les cellules comme indisponibles")  
  
## <a name="set-read-permissions-on-calculated-measures"></a>Définir des autorisations de Lecture sur des mesures calculées  
 Les autorisations sur une mesure calculée peuvent être définies indépendamment de ses parties constituantes. Si vous souhaitez coordonner les autorisations entre une mesure calculée et ses mesures dépendantes, passez à la section suivante sur Lecture du contingent.  
  
 Pour comprendre le fonctionnement des autorisations de Lecture sur une mesure calculée, considérez la mesure **Reseller Gross Profit** dans AdventureWorks. Elle est dérivée des mesures **Reseller Sales Amount** et **Reseller Total Product Cost** . Tant qu'un rôle dispose de l'autorisation Lecture sur les cellules **Reseller Gross Profit** , cette mesure est visible même si des autorisations sont refusées de manière explicite sur les autres mesures. À titre de démonstration, copiez l’expression MDX suivante dans **Créer un rôle** | **Données des cellules** | **Autoriser la lecture du contenu du cube**.  
  
```  
(NOT Measures.CurrentMember IS [Measures].[Reseller Sales Amount])  
AND (NOT Measures.CurrentMember IS [Measures].[Reseller Total Product Cost])  
```  
  
 Dans Excel, connectez-vous au cube à l'aide du rôle actif et choisissez les trois mesures pour voir les effets de la sécurité de cellule. Notez que les mesures de l'ensemble refusé sont indisponibles, tandis que la mesure calculée est visible par l'utilisateur.  
  
 ![Tableau Excel avec disponibles et non cellls](../media/ssas-permscalculatedcells.png "tableau Excel avec cellls disponibles et non disponible")  
  
## <a name="set-read-contingent-permissions-on-calculated-measures"></a>Définir des autorisations de Lecture du contingent sur des mesures calculées  
 La sécurité de cellule offre une alternative, Lecture du contingent, pour définir des autorisations sur les cellules associées qui font partie d'un calcul. Prenez de nouveau l'exemple **Reseller Gross Profit** . Quand, cette fois-ci, vous entrez l’expression MDX fournie dans la section précédente dans la deuxième zone de texte de la boîte de dialogue **Créer un rôle** | **Données des cellules** (dans la zone de texte sous **Autoriser la lecture du contingent de contenu des cellules selon la sécurité des cellules**), le résultat est apparent quand il est affiché dans Excel. Comme **Reseller Gross Profit** dépend de **Reseller Sales Amount** et de **Reseller Total Product Cost**, le bénéfice brut est maintenant inaccessible, car ses parties constituantes sont inaccessibles.  
  
> [!NOTE]  
>  Qu'est-ce qui se produit si vous définissez les autorisations Lecture et Lecture du contingent sur une cellule dans le même rôle ? Le rôle fournira des autorisations de Lecture sur la cellule, et non de Lecture du contingent.  
  
 Nous avons vu dans les sections précédentes que le fait de cocher uniquement la case **Activer les autorisations de lecture du contingent** , sans fournir d’expression MDX, avait pour effet de refuser l’accès à toutes les cellules du cube. Cela est dû au fait que l'ensemble autorisé par défaut est un ensemble vide chaque fois qu' [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] résout un sous-ensemble de cellules de cube.  
  
## <a name="set-readwrite-permissions-on-a-cell"></a>Définir des autorisations de Lecture/Écriture sur une cellule  
 Les autorisations de Lecture/Écriture sur une cellule servent à activer l'écriture différée, à condition que les membres disposent d'autorisations de lecture/écriture sur le cube proprement dit. Les autorisations accordées au niveau des cellules ne peuvent pas être supérieures à celles accordées au niveau du cube. Pour plus d'informations, consultez [Set Partition Writeback](set-partition-writeback.md) .  
  
## <a name="see-also"></a>Voir aussi  
 [Générateur MDX &#40;Analysis Services - Données multidimensionnelles&#41;](../mdx-builder-analysis-services-multidimensional-data.md)   
 [Script MDX de base &#40;MDX&#41;](mdx/the-basic-mdx-script-mdx.md)   
 [Octroyer des autorisations de traitement &#40;Analysis Services&#41;](grant-process-permissions-analysis-services.md)   
 [Octroyer des autorisations sur une dimension &#40;Analysis Services&#41;](grant-permissions-on-a-dimension-analysis-services.md)   
 [Octroyer un accès personnalisé à des données de dimension &#40;Analysis Services&#41;](grant-custom-access-to-dimension-data-analysis-services.md)   
 [Octroyer des autorisations de cube ou de modèle &#40;Analysis Services&#41;](grant-cube-or-model-permissions-analysis-services.md)  
  
  
