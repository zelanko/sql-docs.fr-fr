---
title: Fonction First (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0914520-30c5-4d63-9b59-8d9342ed63b9
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: 57683bf4fe9f4306eecd8bf170510a4b8bd29bb4
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36140238"
---
# <a name="first-function-report-builder-and-ssrs"></a>Fonction First (Générateur de rapports et SSRS)
  Retourne la première valeur dans l'étendue donnée de l'expression spécifiée.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
First(expression, scope)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *expression*  
 (`Variant` ou `Binary`) expression sur laquelle effectuer l’agrégation, par exemple, `=Fields!FieldName.Value`.  
  
 *portée*  
 (`String`) Facultatif. Nom d'un dataset, d'un groupe ou d'une région de données qui contient les éléments de rapport auxquels appliquer la fonction d'agrégation. Si le paramètre *scope* n'est pas spécifié, l'étendue actuelle est utilisée.  
  
## <a name="return-type"></a>Type de retour  
 Déterminé par le type d'expression.  
  
## <a name="remarks"></a>Notes  
 La fonction `First` retourne la première valeur d'un jeu de données après que l'étendue spécifiée a été correctement triée et filtrée.  
  
 Le `First` fonction ne peut pas être utilisée dans les expressions de filtre de groupe de l’étendue actuelle (par défaut).  
  
 Vous pouvez également utiliser `First` dans un en-tête de page pour retourner la première valeur de la `ReportItems` collection pour une page afin de produire des en-têtes de type dictionnaire qui affichent la première et dernière entrées sur une page.  
  
 La valeur du paramètre *scope* doit être une constante de chaîne et ne peut pas être une expression. Pour les agrégats externes ou les agrégats qui ne spécifient pas d'autres agrégats, le paramètre *scope* doit faire référence à l'étendue actuelle ou à une étendue contenante. Pour les agrégats d'agrégats, les agrégats imbriqués peuvent spécifier une étendue enfant.  
  
 *Expression* peut contenir des appels aux fonctions d'agrégation imbriquées avec les exceptions et conditions suivantes :  
  
-   Le paramètre*Scope* des agrégats imbriqués doit être identique à l'étendue de l'agrégat externe ou contenu par celle-ci. Pour toutes les étendues distinctes de l'expression, une étendue doit figurer dans une relation enfant avec toutes les autres étendues.  
  
-   Le paramètre*Scope* des agrégats imbriqués ne peut pas être le nom d'un dataset.  
  
-   *Expression* ne doit pas contenir `First`, `Last`, `Previous`, ou `RunningValue` fonctions.  
  
-   *Expression* ne doit pas contenir les agrégats imbriqués qui spécifient *recursive*.  
  
 Pour plus d’informations, consultez [Référence aux fonctions d’agrégation &#40;Générateur de rapports et SSRS&#41;](report-builder-functions-aggregate-functions-reference.md) et [Étendue des expressions pour les totaux, les agrégats et les collections intégrées &#40;Générateur de rapports et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md).  
  
 Pour plus d’informations sur les agrégats récursifs, consultez [Création de groupes de hiérarchies récursives &#40;Générateur de rapports et SSRS&#41;](creating-recursive-hierarchy-groups-report-builder-and-ssrs.md).  
  
## <a name="example"></a>Exemple  
 L'exemple de code ci-dessous retourne le premier numéro de produit du groupe `Category` d'une région de données :  
  
```  
=First(Fields!ProductNumber.Value, "Category")  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Expression utilise des rapports de &#40;rapport Générateur et SSRS&#41;](expression-uses-in-reports-report-builder-and-ssrs.md)   
 [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md)   
 [Types de données dans les expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Étendue des expressions pour les totaux, les agrégats et les Collections intégrées &#40;rapport Générateur et SSRS&#41;](expression-scope-for-totals-aggregates-and-built-in-collections.md)  
  
  