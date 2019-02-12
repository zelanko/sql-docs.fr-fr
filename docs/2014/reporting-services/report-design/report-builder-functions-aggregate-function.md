---
title: Fonction Aggregate (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- reporting-services-native
ms.topic: conceptual
ms.assetid: 16ce643f-bbb3-40a5-ba78-7aed73156f3e
author: maggiesMSFT
ms.author: maggies
manager: kfile
ms.openlocfilehash: 50a96884a5b97e0e4a287b0c731143dfa2d6e81f
ms.sourcegitcommit: dfb1e6deaa4919a0f4e654af57252cfb09613dd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/11/2019
ms.locfileid: "56029510"
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
 (`String`) Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. *Scope* doit être une constante de type chaîne et ne peut pas être une expression. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Le type de retour est déterminé par le fournisseur de données. La fonction retourne `Nothing` si le fournisseur de données ne prend pas en charge cette fonction ou si les données ne sont pas disponibles.  
  
## <a name="remarks"></a>Notes  
 La fonction `Aggregate` offre un moyen d'utiliser des agrégats calculés sur la source de données externe. La prise en charge de cette fonctionnalité est déterminée par l'extension de données. Par exemple, l'extension pour le traitement des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)] [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)] récupère des ensembles de lignes aplatis d'une requête MDX. Certaines lignes du jeu de résultats peuvent contenir des valeurs d'agrégation calculées sur le serveur de la source de données. Elles sont connues sous le nom d' *agrégats de serveur*. Pour afficher les agrégats de serveur dans le concepteur de requêtes graphique pour [!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], vous pouvez utiliser le bouton **Afficher les agrégations** dans la barre d'outils. Pour plus d’informations, consultez [Interface utilisateur du Concepteur de requêtes MDX Analysis Services &#40;Générateur de rapports&#41;](../analysis-services-mdx-query-designer-user-interface-report-builder.md).  
  
 Lorsque vous affichez la combinaison des valeurs d'agrégation et de dataset détaillées sur les lignes de détails d'une région de données d'un tableau matriciel, les agrégats de serveur ne sont en général pas inclus, car il ne s'agit pas de données de détail. Toutefois, vous pouvez afficher toutes les valeurs récupérées pour le dataset et personnaliser la façon dont les données d'agrégation sont calculées et affichées.  
  
 [!INCLUDE[ssRSnoversion](../../includes/ssrsnoversion-md.md)] détecte l'utilisation de la fonction `Aggregate` dans les expressions de votre rapport pour déterminer s'il convient d'afficher les agrégats de serveur sur les lignes de détails. Si vous incluez `Aggregate` dans une expression d'une région de données, les agrégats de serveur peuvent apparaître uniquement sur les lignes du total de groupe ou du total général, mais pas sur les lignes de détails. Si vous souhaitez afficher les agrégats de serveur sur les lignes de détails, n'utilisez pas la fonction `Aggregate`.  
  
 Vous pouvez modifier ce comportement par défaut en changeant la valeur de l'option **Interpréter les sous-totaux comme des lignes de détails** dans la boîte de dialogue **Propriétés du dataset** . Lorsque cette option a la valeur `True`, toutes les données, y compris les agrégats de serveur, apparaissent comme données de détail. Lorsque cette option a la valeur `False`, les agrégats de serveur apparaissent comme totaux. Le paramètre de cette propriété affecte toutes les régions de données liées à ce dataset.  
  
> [!NOTE]  
>  Tous les groupes contenant l'élément de rapport qui fait référence à `Aggregate` doivent disposer de références de champ simples pour leurs expressions de groupe, par exemple `[FieldName]`. Vous ne pouvez pas utiliser `Aggregate` dans une région de données qui utilise des expressions de groupe complexes. Pour l'extension pour le traitement des données [!INCLUDE[ssNoVersion](../../includes/ssnoversion-md.md)][!INCLUDE[ssASnoversion](../../includes/ssasnoversion-md.md)], votre requête doit inclure des champs MDX de type `LevelProperty` (et non `MemberProperty`) pour prendre en charge l'agrégation à l'aide de la fonction `Aggregate`.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir `First`, `Last`, `Previous`, ou `RunningValue` fonctions.  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="comparing-the-aggregate-and-sum-functions"></a>Comparaison des fonctions Aggregate et Sum  
 La fonction `Aggregate` diffère des fonctions d'agrégation numériques comme `Sum`, car la fonction `Aggregate` retourne une valeur calculée par le fournisseur de données ou l'extension pour le traitement des données. Fonctions d’agrégation numériques comme `Sum` retournent une valeur qui est calculée par le processeur de rapports sur un jeu de données du jeu de données est déterminée par le *étendue* paramètre. Pour plus d’informations, consultez les expressions d’agrégation répertoriées dans [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code suivant affiche une expression qui récupère un agrégat de serveur pour le champ `LineTotal`. L'expression est ajoutée à une cellule d'une ligne qui appartient au groupe `GroupbyOrder`.  
  
```  
=Aggregate(Fields!LineTotal.Value, "GroupbyOrder")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation d’expressions dans les rapports &#40;Générateur de rapport et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  
