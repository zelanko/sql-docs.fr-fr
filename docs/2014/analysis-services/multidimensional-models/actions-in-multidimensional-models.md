---
title: Actions dans les modèles multidimensionnels | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
ms.topic: conceptual
helpviewer_keywords:
- actions [Analysis Services], creating
- report actions [Analysis Services]
- drillthrough actions [Analysis Services]
- cubes [Analysis Services], actions
ms.assetid: b9fee2b9-05a5-4077-848d-d8457326dc27
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: 92291282cfe763c33b548d85e65912b9f3ab6bf9
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084679"
---
# <a name="actions-in-multidimensional-models"></a>Actions dans les modèles multidimensionnels
  Une action est une opération réalisée par un utilisateur final sur un cube (ou portion de cube) sélectionné. Cette opération peut soit démarrer une application en prenant comme paramètre l'élément sélectionné, soit extraire des informations relatives à l'élément sélectionné. Pour plus d’informations sur les d’actions, consultez [Actions &#40;Analysis Services - Données multidimensionnelles&#41;](actions-analysis-services-multidimensional-data.md).  
  
 Pour construire des actions pour un cube, utilisez l’onglet **Actions** du Concepteur de cube. Spécifiez les éléments suivants :  
  
 **Nom**  
 Sélectionnez un nom identifiant l'action.  
  
 **Cible d'action**  
 Sélectionnez l'objet auquel l'action est attachée. Généralement, dans les applications clientes, l'action s'affiche lorsque les utilisateurs finaux sélectionnent l'objet cible ; toutefois, l'application cliente détermine quelle opération de l'utilisateur final affiche les actions. Pour **Type de cible**, sélectionnez l’un des objets suivants :  
  
-   Membres d'attribut  
  
-   Cellules  
  
-   Cube  
  
-   Membres de dimension  
  
-   Hierarchy  
  
-   Membres de hiérarchie  
  
-   Level  
  
-   Membres de niveau  
  
 Après avoir sélectionné le type de l’objet cible, sous **Objet cible**, sélectionnez l’objet de cube du type désigné.  
  
 **Condition (facultatif)**  
 Spécifiez une expression MDX (Multidimensional Expressions) facultative qui est résolue en valeur booléenne. Si la valeur est `True`, l’action est effectuée sur la cible spécifiée. Si la valeur est `False`, l’action n’est pas effectuée.  
  
 **Contenu d'action**  
 Sélectionnez le type d'action. Le tableau suivant récapitule les types disponibles.  
  
|Type|Description|  
|----------|-----------------|  
|Jeu de données|Récupère un dataset.|  
|Propriétaire|Effectue une opération en utilisant une interface différente de celles répertoriées dans ce tableau.|  
|Ensemble de lignes|Récupère un ensemble de lignes.|  
|Instruction|Exécute une commande OLE DB.|  
|URL|Affiche une page qui varie selon le cas dans un navigateur Internet.|  
  
 Pour **Expression d’action**, spécifiez les paramètres qui sont transmis quand l’action est exécutée. La syntaxe doit correspondre à une chaîne et vous devez inclure une expression écrite en MDX. Par exemple, votre expression MDX peut indiquer une partie du cube inclus dans la syntaxe. Les expressions MDX sont évaluées avant la transmission des paramètres. Par ailleurs, vous pouvez utiliser le générateur MDX pour élaborer vos expressions MDX.  
  
 **Propriétés supplémentaires**  
 Sélectionnez la propriété. Le tableau suivant répertorie les propriétés disponibles.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Invocation**|Détermine le mode d'exécution de l'action. Le mode interactif, qui est celui par défaut, spécifie que l'action est exécutée lorsqu'un utilisateur accède à un objet. Les paramètres possibles sont :<br /><br /> Traitement<br /><br /> Interactif<br /><br /> À l’ouverture|  
|**Application**|Décrit l'application de l'action.|  
|**Description**|Décrit l'action.|  
|**Légende**|Fournit une légende qui s'affiche pour l'action. Si la légende est MDX, spécifiez `True` pour **légende est MDX**.|  
|**La légende est MDX**|Spécifiez `True` si la légende est MDX ou `False` si elle n’est pas.|  
  
> [!NOTE]  
>  Vous devez utiliser le langage de script Analysis Services (ASSL) ou les objets AMO (Analysis Management Objects) pour définir les types d'action de ligne de commande et HTML. Pour plus d’informations, consultez [Élément Action &#40;ASSL&#41;](../scripting/objects/action-element-assl.md), [Élément Type &#40;Action&#41; &#40;ASSL&#41;](../scripting/properties/type-element-action-assl.md) et [Programmation d’objets OLAP AMO avancés](analysis-management-objects/programming-amo-olap-advanced-objects.md).  
  
## <a name="creating-a-reporting-action"></a>Création d'une action de rapport  
 Le serveur de rapports répond aux demandes de rapports basées sur une URL. Pour créer une action de rapport, dans le menu **Cube** , cliquez sur **Nouvelle action de rapport**. Les options suivantes sont propres à une action de rapport.  
  
 **Serveur de rapports**  
 Les propriétés décrites dans le tableau suivant sont spécifiées pour le serveur de rapports.  
  
|Propriété|Description|  
|--------------|-----------------|  
|**Nom du serveur**|Nom de l'ordinateur exécutant le serveur de rapports.|  
|**Chemin d'accès au serveur**|Chemin exposé par le serveur de rapports.|  
|**Format de rapport**|HTML5, HTML3, Excel ou PDF.|  
  
 **Paramètres (facultatif)**  
 Les paramètres sont envoyés au serveur comme une partie de la chaîne de l'URL lorsque l'action est créée. Ceux-ci comptent notamment **Nom du paramètre** et **Valeur du paramètre**, c’est-à-dire une expression MDX.  
  
 L'URL du serveur de rapports est construite comme suit :  
  
```  
  
http://  
host  
/  
virtualdirectory  
/Path&  
parametername1  
=  
parametervalue1  
& ...  
```  
  
 Exemple :  
  
```  
http://localhost/ReportServer/Sales/YearlySalesByCategory?rs:Command=Render&Region=West  
```  
  
## <a name="creating-a-drillthrough-action"></a>Création d'une action d'extraction  
 Une action d'extraction est définie par une action de type ensemble de lignes, qui est retournée à l'application cliente comme une instruction d'extraction. La cible d'action est le membre d'un groupe de mesures. Pour créer une action d’extraction, dans le menu **Cube** , cliquez sur **Nouvelle action d’extraction**. Les options suivantes sont propres à une action d'extraction.  
  
 **Colonnes d'extraction**  
 Sélectionnez une ou plusieurs dimensions et, pour chacune d'entre elles, les colonnes d'extraction retournées à l'application cliente par l'action.  
  
## <a name="see-also"></a>Voir aussi  
 [Cubes dans les modèles multidimensionnels](cubes-in-multidimensional-models.md)  
  
  
