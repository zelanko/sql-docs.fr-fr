---
title: Instruction CREATE SET (MDX) | Documents Microsoft
ms.custom: ''
ms.date: 03/02/2016
ms.prod: analysis-services
ms.prod_service: analysis-services
ms.service: ''
ms.component: ''
ms.reviewer: ''
ms.suite: pro-bi
ms.technology: ''
ms.tgt_pltfrm: ''
ms.topic: language-reference
f1_keywords:
- SET
- CREATE SET
- CREATE_SET
- CREATE
dev_langs:
- kbMDX
helpviewer_keywords:
- named sets [MDX]
- CREATE SET statement
ms.assetid: eff51eeb-5e7e-4706-b861-c57b6f3f89f0
caps.latest.revision: 42
author: Minewiskan
ms.author: owend
manager: erikre
ms.workload: Inactive
ms.openlocfilehash: c709890d1c9e9ff3b1e6351fc4b62e067e12a864
ms.sourcegitcommit: f486d12078a45c87b0fcf52270b904ca7b0c7fc8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/08/2018
---
# <a name="mdx-data-definition---create-set"></a>Définition de données MDX - créer défini
[!INCLUDE[ssas-appliesto-sqlas](../includes/ssas-appliesto-sqlas.md)]

  Crée un jeu nommé avec une étendue de session pour le cube actuel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
CREATE [SESSION] [ STATIC | DYNAMIC ] [HIDDEN] SET   
   CURRENTCUBE | Cube_Name  
      .Set_Name AS 'Set_Expression'  
      [,Property_Name = Property_Value, ...n]  
```  
  
## <a name="arguments"></a>Arguments  
 *Cube_Name*  
 Expression de chaîne valide qui précise le nom du cube.  
  
 *Set_Name*  
 Expression de chaîne valide qui précise le nom du jeu nommé en cours de création.  
  
 *Set_Expression*  
 Une expression MDX (Multidimensional Expressions) valide qui retourne un jeu.  
  
 *Property_name*  
 Chaîne valide qui fournit le nom d'une propriété de jeu.  
  
 *Nom*  
 Expression scalaire valide qui définit la valeur de la propriété de jeu.  
  
## <a name="remarks"></a>Notes   
 Un jeu nommé est un jeu de membres de dimension (ou une expression définissant un jeu) que vous créez pour le réutiliser. Par exemple, un jeu nommé vous permet de définir un jeu de membres de dimension constitué de l'ensemble des dix premiers magasins en termes de ventes. Ce jeu peut être défini statiquement, ou au moyen d’une fonction comme [TopCount](../mdx/topcount-mdx.md). Ce jeu nommé peut ensuite être utilisé chaque fois que l'ensemble des 10 premiers magasins est nécessaire.  
  
 L’instruction CREATE SET crée un jeu nommé qui demeure disponible durant toute la session et peut donc être utilisée dans plusieurs requêtes dans une session. Pour plus d’informations, consultez [Creating Session-Scoped de membres calculés &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-calculated-members-session-scoped-calculated-members.md).  
  
 Vous pouvez également définir un jeu nommé pour une seule requête. Pour ce faire, utilisez la clause WITH dans l'instruction SELECT. Pour plus d’informations sur la clause WITH, consultez [Creating Query-Scoped les jeux nommés &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 Le *Set_Expression* clause peut contenir n’importe quelle fonction qui prend en charge la syntaxe MDX. Les jeux créés avec l'instruction CREATE SET qui ne spécifient pas la clause SESSION ont une étendue de session. Utilisez la clause WITH pour créer un jeu avec une étendue de requête.  
  
 La spécification d'un cube autre que le cube actuellement connecté génère une erreur. C'est pourquoi vous devez utiliser CURRENTCUBE de préférence à un nom de cube, pour désigner le cube actuel.  
  
## <a name="scope"></a>Portée  
 Un jeu défini par l'utilisateur peut se produire avec l'une des étendues répertoriées dans le tableau ci-dessous.  
  
 Étendue de requête  
 La visibilité et la durée de vie du jeu sont limitées à la requête. Le jeu est défini dans une requête distincte. L'étendue de requête remplace l'étendue de session. Pour plus d’informations, consultez [Creating Query-Scoped les jeux nommés &#40; MDX &#41; ](../analysis-services/multidimensional-models/mdx/mdx-named-sets-creating-query-scoped-named-sets.md).  
  
 Étendue de session  
 La visibilité et la durée de vie du jeu sont limitées à la session dans laquelle il est créé. (La durée de vie est inférieure à la durée de la session si une instruction DROP SET est émise sur le jeu.) L'instruction CREATE SET crée un jeu avec une étendue de session. Utilisez la clause WITH pour créer un jeu avec une étendue de requête.  
  
### <a name="example"></a> Exemple  
 L'exemple ci-dessous crée un jeu appelé Core Products (produits clés). La requête SELECT démontre ensuite l'appel du nouveau jeu créé. Vous devez exécuter l'instruction CREATE SET avant d'exécuter la requête SELECT. Ces deux éléments ne peuvent pas être exécutés dans le même traitement.  
  
```  
CREATE SET [Adventure Works].[Core Products] AS '{[Product].[Category].[Bikes]}'  
  
SELECT [Core Products] ON 0  
  FROM [Adventure Works]  
```  
  
## <a name="set-evaluation"></a>Évaluation du jeu  
 L'évaluation du jeu peut être définie pour se produire différemment ; elle peut être définie pour se produire une seule fois au moment de la création du jeu, ou bien à chaque fois que le jeu est utilisé.  
  
 STATIC  
 Indique que le jeu n'est évalué qu'au moment de l'évaluation de l'instruction CREATE SET.  
  
 DYNAMIC  
 Indique que le jeu doit être évalué à chaque fois qu'il est utilisé dans une requête.  
  
## <a name="set-visibility"></a>Visibilité du jeu  
 Le jeu peut être visible ou non pour les autres utilisateurs qui interrogent le cube.  
  
 HIDDEN  
 Indique que le jeu n'est pas visible pour les utilisateurs qui interrogent le cube.  
  
## <a name="standard-properties"></a>Propriétés standard  
 Chaque jeu possède un jeu de propriétés par défaut. Lorsqu’une application cliente est connectée à [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], les propriétés par défaut sont pris en charge, soit disponible pour être pris en charge, comme l’administrateur choisit.  
  
|Identificateur de propriété|Signification|  
|-------------------------|-------------|  
|CAPTION|Chaîne que l'application cliente utilise pour la légende du jeu.|  
|DISPLAY_FOLDER|Chaîne qui identifie le chemin d'accès du dossier d'affichage que l'application cliente utilise pour afficher le jeu. Le séparateur de niveau de dossier est défini par l'application cliente. Pour les outils et les clients fournis par [!INCLUDE[ssASnoversion](../includes/ssasnoversion-md.md)], la barre oblique inverse (\\) est le séparateur de niveau. Pour attribuer différents dossiers d'affichage à un jeu défini, utilisez un point-virgule (;) pour les séparer.|  
  
## <a name="see-also"></a>Voir aussi  
 [Supprimez l’instruction SET &#40; MDX &#41;](../mdx/mdx-data-definition-drop-set.md)   
 [Instructions MDX de définition de données &#40; MDX &#41;](../mdx/mdx-data-definition-statements-mdx.md)  
  
  
