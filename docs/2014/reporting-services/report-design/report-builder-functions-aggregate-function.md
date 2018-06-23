---
title: Fonction Aggregate (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 3d05f8d71c3ce12722f139429e48a2a48e8efd8e
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140223"
---
# <a name="aggregate-function-report-builder-and-ssrs"></a>Fonction d'agrégation (Générateur de rapports et SSRS)
  Retourne un agrégat personnalisé de l'expression spécifiée, comme défini par le fournisseur de données.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Aggregate(expression, scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 Expression sur laquelle effectuer l'agrégation. Elle doit être une référence de champ simple.  
  
 *portée*  
 (`String`) Le nom d’une région de données, groupe ou groupe de données qui contient le rapport d’éléments auxquels appliquer la fonction d’agrégation. *Scope* doit être une constante de type chaîne et ne peut pas être une expression. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Le type de retour est déterminé par le fournisseur de données. Retourne `Nothing` si le fournisseur de données ne prend pas en charge cette fonction ou de données ne seront pas disponibles.  
  
## <a name="remarks"></a>Notes  
 La fonction `Aggregate` offre un moyen d'utiliser des agrégats calculés sur la source de données externe. La prise en charge de cette fonctionnalité est déterminée par l'extension de données. Par exemple, l'extension pour le traitement des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] récupère des ensembles de lignes aplatis d'une requête MDX. Certaines lignes du jeu de résultats peuvent contenir des valeurs d'agrégation calculées sur le serveur de la source de données. Elles sont connues sous le nom d' *agrégats de serveur*. Pour afficher les agrégats de serveur dans le concepteur de requêtes graphique pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser le bouton **Afficher les agrégations** dans la barre d'outils. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes MDX Analysis Services &#40;Générateur de rapports&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).  
  
 Lorsque vous affichez la combinaison des valeurs d'agrégation et de dataset détaillées sur les lignes de détails d'une région de données d'un tableau matriciel, les agrégats de serveur ne sont en général pas inclus, car il ne s'agit pas de données de détail. Toutefois, vous pouvez afficher toutes les valeurs récupérées pour le dataset et personnaliser la façon dont les données d'agrégation sont calculées et affichées.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] détecte l’utilisation de la `Aggregate` fonction dans des expressions dans votre rapport afin de déterminer s’il faut afficher les agrégats de serveur sur les lignes de détails. Si vous incluez `Aggregate` dans une expression dans une région de données, les agrégats de serveur peuvent apparaître uniquement sur le groupe total ou du nombre total de lignes, pas sur les lignes de détails. Si vous souhaitez afficher les agrégats de serveur sur les lignes de détails, n'utilisez pas la fonction `Aggregate`.  
  
 Vous pouvez modifier ce comportement par défaut en changeant la valeur de l'option **Interpréter les sous-totaux comme des lignes de détails** dans la boîte de dialogue **Propriétés du dataset** . Lorsque cette option a la valeur `True`, toutes les données, y compris les agrégats de serveur, apparaissent comme données de détail. Lorsque cette option a la valeur `False`, les agrégats de serveur apparaissent comme totaux. Le paramètre de cette propriété affecte toutes les régions de données liées à ce dataset.  
  
> [!NOTE]  
>  Tous les groupes contenant l'élément de rapport qui fait référence à `Aggregate` doivent disposer de références de champ simples pour leurs expressions de groupe, par exemple `[FieldName]`. Vous ne pouvez pas utiliser `Aggregate` dans une région de données qui utilise des expressions de groupe complexes. Pour le [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] extension pour le traitement de données, votre requête doit inclure des champs MDX de type `LevelProperty` (pas `MemberProperty`) pour prendre en charge l’agrégation à l’aide du `Aggregate`(fonction).  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir `First`, `Last`, `Previous`, ou `RunningValue` fonctions.  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a>Comparaison des fonctions Aggregate et Sum  
 Le `Aggregate` diffère des fonctions d’agrégation numériques comme `Sum` dans la mesure où le `Aggregate` fonction retourne une valeur calculée par l’extension de données fournisseur ou le traitement des données. Les fonctions d’agrégation numériques comme `Sum` retournent une valeur calculée par le processeur de rapports sur un jeu de données à partir du jeu de données est déterminée par le *étendue* paramètre. Pour plus d’informations, consultez les expressions d’agrégation répertoriées dans [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant affiche une expression qui récupère un agrégat de serveur pour le champ `LineTotal`. L'expression est ajoutée à une cellule d'une ligne qui appartient au groupe `GroupbyOrder`.  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  