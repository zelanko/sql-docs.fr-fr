---
title: Références à la collection Parameters (Générateur de rapports et SSRS) | Microsoft Docs
ms.custom: ''
ms.date: 03/08/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- reporting-services-native
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c4b47e15-0484-4c13-9182-898db825f01f
caps.latest.revision: 7
author: douglaslM
ms.author: douglasl
manager: mblythe
ms.openlocfilehash: a036b16073f19c106b507653921185fcb8df0bbd
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36153872"
---
# <a name="parameters-collection-references-report-builder-and-ssrs"></a>Références à la collection Parameters (Générateur de rapports et SSRS)
  Les paramètres de rapport font partie des collections intégrées que vous pouvez référencer à partir d'une expression. En incluant des paramètres dans une expression, vous pouvez personnaliser les données et l'apparence d'un rapport en fonction des choix faits par un utilisateur. Des expressions peuvent être utilisées pour toutes les propriétés des éléments de rapport ou propriétés des zones de texte qui comportent l’option (*Fx*) ou \<**Expression**>. Les expressions sont également utilisées pour contrôler différemment le contenu et l'apparence d'un rapport. Pour plus d’informations, consultez [Exemples d’expressions &#40;Générateur de rapports et SSRS&#41;](expression-examples-report-builder-and-ssrs.md).  
  
 Lorsque vous comparez des valeurs de paramètres à des valeurs de champs de dataset au moment de l'exécution, les types de données des deux éléments que vous comparez doivent être identiques. Les paramètres de rapport peuvent être de l'un des types suivants : Booléen, DateTime, Entier, Float ou Texte, qui représente le type de données sous-jacent Chaîne. Si nécessaire, vous pouvez convertir le type de données de la valeur du paramètre pour qu'il corresponde à la valeur du dataset. Pour plus d’informations, consultez [des Types de données dans les Expressions &#40;le Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md).  
  
 Pour inclure une référence de paramètre dans une expression, vous devez comprendre comment spécifier la syntaxe correcte pour la référence de paramètre, laquelle varie suivant que le paramètre est un paramètre à valeur unique ou à valeurs multiples.  
  
> [!NOTE]  
>  [!INCLUDE[ssRBRDDup](../../includes/ssrbrddup-md.md)]  
  
##  <a name="Single"></a> Utilisation d'un paramètre à valeur unique dans une expression  
 Le tableau suivant présente des exemples de la syntaxe à utiliser lorsque vous incluez une référence à un paramètre à valeur unique de n'importe quel type de données dans une expression.  
  
|Exemple|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<Nom_paramètre>* `.IsMultiValue`|Retourne `False`.<br /><br /> Vérifie si un paramètre est à valeurs multiples. Si `True`, le paramètre est à valeurs multiples, et il s’agit d’une collection d’objets. Si `False`, le paramètre est la valeur unique et est un objet unique.|  
|`=Parameters!` *\<Nom_paramètre>* `.Count`|Retourne la valeur entière 1. Pour un paramètre à valeur unique, le nombre est toujours 1.|  
|`=Parameters!` *\<Nom_paramètre>* `.Label`|Retourne l'étiquette du paramètre, qui est souvent utilisée comme nom complet dans une liste déroulante de valeurs disponibles.|  
|`=Parameters!` *\<Nom_paramètre>* `.Value`|Retourne la valeur du paramètre. Si la propriété Libellé n’a pas été définie, cette valeur apparaît dans la liste déroulante des valeurs disponibles.|  
|`=CStr(Parameters!`  *\<Nom_paramètre>* `.Value)`|Retourne la valeur du paramètre sous forme de chaîne.|  
|`=Fields(Parameters!` *\<Nom_paramètre>* `.Value).Value`|Retourne la valeur du champ qui possède le même nom que le paramètre.|  
  
 Pour plus d’informations sur l’utilisation de paramètres dans un filtre, consultez [Ajouter des filtres de datasets, des filtres de régions de données et des filtres de groupes &#40;Générateur de rapports et SSRS&#41;](add-dataset-filters-data-region-filters-and-group-filters.md).  
  
##  <a name="Multi"></a> Utilisation d'un paramètre à valeurs multiples dans une expression  
 Le tableau suivant présente des exemples de la syntaxe à utiliser lorsque vous incluez une référence à un paramètre à valeurs multiples de n'importe quel type de données dans une expression.  
  
|Exemple|Description|  
|-------------|-----------------|  
|`=Parameters!` *\<Nom_paramètre_à_valeurs_multiples>* `.IsMultiValue`|Retourne `True` ou `False`.<br /><br /> Vérifie si un paramètre est à valeurs multiples. Si la valeur retournée est `True`, le paramètre est à valeurs multiples et il s'agit d'une collection d'objets. Si la valeur retournée est `False`, le paramètre est à valeur unique et il s'agit d'un seul objet.|  
|`=Parameters!` *\<Nom_paramètre_à_valeurs_multiples>* `.Count`|Retourne une valeur entière.<br /><br /> Fait référence au nombre de valeurs. Pour un paramètre à valeur unique, le nombre est toujours 1. Pour un paramètre à valeurs multiples, le nombre est 0 ou plus.|  
|`=Parameters!` *\<Nom_paramètre_à_valeurs_multiples>* `.Value(0)`|Retourne la première valeur dans un paramètre à valeurs multiples.|  
|`=Parameters!` *\<Nom_paramètre_à_valeurs_multiples>* `.Value(Parameters!`  *\<Nom_paramètre_à_valeurs_multiples>*`.Count-1)`|Retourne la dernière valeur dans un paramètre à valeurs multiples.|  
|`=Split("Value1,Value2,Value3",",")`|Retourne un tableau de valeurs.<br /><br /> Permet de créer un tableau de valeurs pour un paramètre de type `String` à valeurs multiples. Vous pouvez utiliser un délimiteur dans le second paramètre pour établir un fractionnement (Split). Cette expression peut être utilisée pour définir les valeurs par défaut d'un paramètre à valeurs multiples ou pour créer un paramètre à valeurs multiples à envoyer à un rapport d'extraction ou de type sous-rapport.|  
|`=Join(Parameters!` *\<Nom_paramètre_à_valeurs_multiples>* `.Value,", ")`|Retourne un `String` qui se compose d’une liste délimitée par des virgules des valeurs dans un paramètre à valeurs multiples. Vous pouvez utiliser un délimiteur dans le second paramètre pour établir une liaison (Join).|  
  
 Pour plus d’informations sur l’utilisation de paramètres dans un filtre, consultez [Paramètres de rapport &#40;Générateur de rapports et Concepteur de rapports&#41;](report-parameters-report-builder-and-report-designer.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Expressions &#40;Générateur de rapports et SSRS&#41;](expressions-report-builder-and-ssrs.md)   
 [Filtres couramment utilisés &#40;Générateur de rapports et SSRS&#41;](commonly-used-filters-report-builder-and-ssrs.md)   
 [Ajouter, modifier ou supprimer un paramètre de rapport &#40;rapport Générateur et SSRS&#41;](add-change-or-delete-a-report-parameter-report-builder-and-ssrs.md)   
 [Didacticiel : ajouter un paramètre à un rapport &#40;Générateur de rapports&#41;](../tutorial-add-a-parameter-to-your-report-report-builder.md)   
 [Didacticiels &#40;Générateur de rapports&#41;](../report-builder-tutorials.md)   
 [Collections intégrées dans les Expressions &#40;rapport Générateur et SSRS&#41;](built-in-collections-in-expressions-report-builder.md)  
  
  