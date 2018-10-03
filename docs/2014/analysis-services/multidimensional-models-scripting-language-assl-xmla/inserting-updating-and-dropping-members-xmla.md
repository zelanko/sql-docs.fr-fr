---
title: Insertion, mise à jour et suppression de membres (XMLA) | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology:
- analysis-services
- docset-sql-devref
ms.topic: reference
helpviewer_keywords:
- inserting dimension members
- XML for Analysis, members
- removing dimension members
- dropping dimension members
- write-enabled dimensions [Analysis Services]
- XMLA, members
- deleting dimension members
- dimensions [Analysis Services], XML for Analysis
ms.assetid: bba922b5-8b88-4051-9506-ff055248182a
author: minewiskan
ms.author: owend
manager: craigg
ms.openlocfilehash: d035cf5891c12857fcdcbc2da7df2304eb10dcdb
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48171489"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>Insertion, mise à jour et suppression de membres (XMLA)
  Vous pouvez utiliser la [insérer](../xmla/xml-elements-commands/insert-element-xmla.md), [mettre à jour](../xmla/xml-elements-commands/update-element-xmla.md), et [Drop](../xmla/xml-elements-commands/drop-element-xmla.md) commandes XML for Analysis (XMLA) pour respectivement, insérer, mettre à jour ou supprimer des membres dans une dimension activée en écriture. Pour plus d’informations sur les dimensions activées en écriture, consultez [Write Dimensions](../multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="inserting-new-members"></a>Insertion de nouveaux membres  
 La commande `Insert` permet d'insérer de nouveaux membres dans les attributs spécifiés d'une dimension activée en écriture.  
  
 Avant de construire la commande `Insert`, vous devez disposer des informations suivantes pour les nouveaux membres à insérer :  
  
-   la dimension dans laquelle les nouveaux membres doivent être insérés ;  
  
-   l'attribut de dimension dans lequel insérer les nouveaux membres ;  
  
-   les noms des nouveaux membres, y compris les éventuelles traductions applicables au nom ;  
  
-   les clés des nouveaux membres. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
-   les valeurs des propriétés d'attribut applicables qui ne sont pas implémentées en tant qu'autres attributs au sein de la dimension. Ces propriétés d'attribut peuvent consister en des opérations unaires, des traductions, des cumuls personnalisés, des propriétés de cumul personnalisé et des niveaux ignorés.  
  
 La commande `Insert` prend uniquement deux propriétés :  
  
-   Le [objet](../xmla/xml-elements-properties/object-element-xmla.md) propriété, qui contient une référence d’objet pour la dimension dans lequel les membres doivent être insérés. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   Le [attributs](../xmla/xml-elements-properties/attributes-element-xmla.md) propriété, qui contient un ou plusieurs [attribut](../xmla/xml-elements-properties/attribute-element-xmla.md) éléments pour identifier les attributs dans lequel les membres doivent être insérés. Chaque élément `Attribute` identifie un attribut et fournit le nom, la valeur, les traductions, l'opérateur unaire, le cumul personnalisé, les propriétés de cumul personnalisé et les niveaux ignorés du membre unique à ajouter à l'attribut identifié.  
  
    > [!NOTE]  
    >  Toutes les propriétés de l'élément `Attribute` doivent être incluses. Sinon, une erreur risque de se produire.  
  
## <a name="updating-existing-members"></a>Mise à jour de membres existants  
 La commande `Update` permet de mettre à jour les membres existants des attributs spécifiés, en tenant compte des relations avec les autres membres des autres attributs, dans une dimension activée en écriture. La commande `Update` permet de déplacer des membres vers d'autres niveaux dans les hiérarchies contenues dans la dimension, et elle peut être utilisée pour restructurer les hiérarchies parent-enfant définies dans les attributs parents.  
  
 Avant de construire la commande `Update`, vous devez disposer des informations suivantes pour les membres à mettre à jour :  
  
-   la dimension dans laquelle les membres existants doivent être mis à jour ;  
  
-   les attributs de la dimension dans lesquels les membres existants doivent être mis à jour ;  
  
-   les clés des membres existants. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
-   les valeurs des propriétés d'attribut applicables qui ne sont pas implémentées en tant qu'autres attributs au sein de la dimension. Ces propriétés d'attribut peuvent consister en des opérations unaires, des traductions, des cumuls personnalisés, des propriétés de cumul personnalisé et des niveaux ignorés.  
  
 La commande `Update` ne prend que trois propriétés (obligatoires) :  
  
-   La propriété `Object`, qui contient une référence d'objet pour la dimension dont les membres doivent être mis à jour. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   La propriété `Attributes`, qui contient un ou plusieurs éléments `Attribute` pour identifier les attributs dont les membres doivent être mis à jour. L'élément `Attribute` identifie un attribut et fournit le nom, la valeur, les traductions, l'opérateur unaire, le cumul personnalisé, les propriétés de cumul personnalisé et les niveaux ignorés du membre unique à mettre à jour pour l'attribut identifié.  
  
    > [!NOTE]  
    >  Toutes les propriétés de l'élément `Attribute` doivent être incluses. Sinon, une erreur risque de se produire.  
  
-   Le [où](../xmla/xml-elements-properties/where-element-xmla.md) propriété, qui contient un ou plusieurs `Attribute` éléments qui limitent les attributs dans lequel les membres doivent être mis à jour. Le `Where` propriété est essentielle de limiter un `Update` commande à des instances spécifiques d’un membre. Si le `Where` propriété n’est pas spécifiée, toutes les instances d’un membre donné sont mises à jour. Par exemple, supposons que vous voulez modifier le nom de la ville de trois clients (Bellevue à la place de Redmond). Pour changer le nom de la ville, vous devez fournir une propriété `Where` qui identifie les trois membres de l'attribut Customer (Client) dont les membres de l'attribut City (Ville) doivent être modifiés. Si vous ne fournissez pas cette propriété `Where`, tous les clients dont le nom de ville actuel est Redmond seront associés au nom de ville Bellevue une fois la commande `Update` exécutée.  
  
    > [!NOTE]  
    >  À l'exception des nouveaux membres, la commande `Update` ne peut mettre à jour que les valeurs de clé des attributs non inclus dans la clause `Where`. Par exemple, le nom de ville ne peut pas être mis à jour lors de la mise à jour d'un client ; sinon, le nom de ville est modifié pour tous les clients.  
  
### <a name="updating-members-in-parent-attributes"></a>Mise à jour des membres d'attributs parents  
 Pour prendre en charge les attributs parents, le `Update` commande facultatif [MoveWithDescendants](../xmla/xml-elements-properties/movewithdescendants-element-xmla.md)propriété. Le fait de définir la propriété `MoveWithDescendants` à true indique que les descendants du membre parent doivent également être déplacés avec le membre parent lorsque l'identificateur de ce dernier est modifié. Si cette valeur est définie à false, le déplacement d'un membre parent entraîne la promotion des descendants immédiats de ce membre parent au niveau précédent du membre parent.  
  
 Lors de la mise à jour des membres d'un attribut parent, la commande `Update` ne peut pas mettre à jour les membres des autres attributs.  
  
## <a name="dropping-existing-members"></a>Suppression de membres existants  
 Avant de construire la commande `Drop`, vous devez disposer des informations suivantes pour les membres à supprimer :  
  
-   La dimension dans laquelle les membres existants doivent être supprimés.  
  
-   Les attributs de la dimension dans lesquels les membres existants doivent être supprimés.  
  
-   Les clés des membres existants à supprimer. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
 La commande `Drop` ne prend que deux propriétés (obligatoires) :  
  
-   La propriété `Object`, qui contient une référence d'objet pour la dimension dans laquelle les membres doivent être supprimés. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   La propriété `Where`, qui contient un ou plusieurs éléments `Attribute` pour limiter les attributs dont les membres doivent être supprimés. La propriété `Where` s'avère indispensable pour limiter une commande `Drop` aux instances spécifiques d'un membre. Si la commande `Where`n'est pas spécifiée, toutes les instances d'un membre donné sont supprimées. Par exemple, supposons que vous voulez supprimer tois clients de la ville de Redmond. Pour supprimer ces clients, vous devez fournir une propriété `Where` qui identifie les trois membres de l'attribut Customer (Client) à supprimer et le membre Redmond de l'attribut City (Ville) auquel sont associés les trois clients à supprimer. Si la propriété `Where` ne spécifie que le membre Redmond de l'attribut City, tous les clients associés à Redmond sont supprimés par la commande `Drop`. Si la propriété `Where` ne spécifie que les trois membres de l'attribut Customer, les trois clients sont bel et bien supprimés par la commande `Drop`.  
  
    > [!NOTE]  
    >  Les éléments `Attribute` inclus dans une commande `Drop` ne doivent contenir que les propriétés `AttributeName` et `Keys`. Sinon, une erreur risque de se produire.  
  
### <a name="dropping-members-in-parent-attributes"></a>Suppression de membres d'attributs parents  
 Définition de la [DeleteWithDescendants](../xmla/xml-elements-properties/deletewithdescendants-element-xmla.md) propriété indique que les descendants d’un membre parent doivent également être supprimés avec le membre parent. Si cette valeur est définie à false, les descendants immédiats du membre parent sont alors promus au niveau antérieur du membre parent.  
  
> [!IMPORTANT]  
>  Un utilisateur n'a besoin que d'autorisations de suppression du membre parent pour pouvoir supprimer à la fois le membre parent et ses descendants. Il n'a pas besoin d'autorisations de suppression des descendants.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DROP &#40;XMLA&#41;](../xmla/xml-elements-commands/drop-element-xmla.md)   
 [Insérer un élément &#40;XMLA&#41;](../xmla/xml-elements-commands/insert-element-xmla.md)   
 [Mettre à jour d’élément &#40;XMLA&#41;](../xmla/xml-elements-commands/update-element-xmla.md)   
 [Définition et identification d’objets &#40;XMLA&#41;](../xmla/xml-elements-objects.md)   
 [Développement avec XMLA dans Analysis Services](developing-with-xmla-in-analysis-services.md)  
  
  
