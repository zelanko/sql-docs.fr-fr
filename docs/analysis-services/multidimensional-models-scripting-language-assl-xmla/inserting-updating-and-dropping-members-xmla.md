---
title: Insertion, mise à jour et suppression de membres (XMLA) | Microsoft Docs
ms.date: 05/02/2018
ms.prod: sql
ms.technology: analysis-services
ms.custom: xmla
ms.topic: conceptual
ms.author: owend
ms.reviewer: owend
author: minewiskan
manager: kfile
ms.openlocfilehash: 3a409e21e925b3912aee5ec751747f61bce05276
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63138581"
---
# <a name="inserting-updating-and-dropping-members-xmla"></a>Insertion, mise à jour et suppression de membres (XMLA)
  Vous pouvez utiliser la [insérer](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla), [mettre à jour](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla), et [Drop](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla) commandes XML for Analysis (XMLA) pour respectivement, insérer, mettre à jour ou supprimer des membres dans une dimension activée en écriture. Pour plus d’informations sur les dimensions activées en écriture, consultez [Write Dimensions](../../analysis-services/multidimensional-models-olap-logical-dimension-objects/write-enabled-dimensions.md).  
  
## <a name="inserting-new-members"></a>Insertion de nouveaux membres  
 Le **insérer** commande insère de nouveaux membres dans les attributs spécifiés dans une dimension activée en écriture.  
  
 Avant de construire le **insérer** commande, vous devez disposer des informations suivantes pour les nouveaux membres à insérer :  
  
-   la dimension dans laquelle les nouveaux membres doivent être insérés ;  
  
-   l'attribut de dimension dans lequel insérer les nouveaux membres ;  
  
-   les noms des nouveaux membres, y compris les éventuelles traductions applicables au nom ;  
  
-   les clés des nouveaux membres. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
-   les valeurs des propriétés d'attribut applicables qui ne sont pas implémentées en tant qu'autres attributs au sein de la dimension. Ces propriétés d'attribut peuvent consister en des opérations unaires, des traductions, des cumuls personnalisés, des propriétés de cumul personnalisé et des niveaux ignorés.  
  
 Le **insérer** commande accepte uniquement deux propriétés :  
  
-   Le [objet](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/object-element-xmla) propriété, qui contient une référence d’objet pour la dimension dans lequel les membres doivent être insérés. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   Le [attributs](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attributes-element-xmla) propriété, qui contient un ou plusieurs [attribut](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/attribute-element-xmla) éléments pour identifier les attributs dans lequel les membres doivent être insérés. Chaque **attribut** élément identifie un attribut et fournit le nom, valeur, traductions, opérateur unaire, cumul personnalisé, propriétés de cumul personnalisé et des niveaux pour un seul membre à ajouter à l’attribut identifié ignorés.  
  
    > [!NOTE]  
    >  Toutes les propriétés pour le **attribut** élément doit être inclus. Sinon, une erreur risque de se produire.  
  
## <a name="updating-existing-members"></a>Mise à jour de membres existants  
 Le **mise à jour** commande met à jour des membres existants dans les attributs spécifiés, en fonction des relations avec d’autres membres dans d’autres attributs, dans une dimension activée en écriture. Le **mise à jour** commande peut déplacer des membres vers d’autres niveaux dans les hiérarchies contient dans la dimension et peuvent être utilisées pour restructurer les hiérarchies parent-enfant définies par les attributs parents.  
  
 Avant de construire le **mise à jour** commande, vous devez disposer des informations suivantes pour les membres à mettre à jour :  
  
-   la dimension dans laquelle les membres existants doivent être mis à jour ;  
  
-   les attributs de la dimension dans lesquels les membres existants doivent être mis à jour ;  
  
-   les clés des membres existants. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
-   les valeurs des propriétés d'attribut applicables qui ne sont pas implémentées en tant qu'autres attributs au sein de la dimension. Ces propriétés d'attribut peuvent consister en des opérations unaires, des traductions, des cumuls personnalisés, des propriétés de cumul personnalisé et des niveaux ignorés.  
  
 Le **mise à jour** commande accepte uniquement trois propriétés obligatoires :  
  
-   Le **objet** propriété, qui contient une référence d’objet pour la dimension dans lequel les membres doivent être mis à jour. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   Le **attributs** propriété, qui contient un ou plusieurs **attribut** éléments pour identifier les attributs dans lequel les membres doivent être mis à jour. Le **attribut** élément identifie un attribut et fournit le nom, valeur, traductions, opérateur unaire, cumul personnalisé, propriétés de cumul personnalisé et des niveaux ignorés pour un seul membre mis à jour pour l’attribut identifié.  
  
    > [!NOTE]  
    >  Toutes les propriétés pour le **attribut** élément doit être inclus. Sinon, une erreur risque de se produire.  
  
-   Le [où](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/where-element-xmla) propriété, qui contient un ou plusieurs **attribut** éléments qui limitent les attributs dans lequel les membres doivent être mis à jour. Le **où** propriété est essentielle de limiter un **mise à jour** commande à des instances spécifiques d’un membre. Si le **où** propriété n’est pas spécifiée, toutes les instances d’un membre donné sont mises à jour. Par exemple, supposons que vous voulez modifier le nom de la ville de trois clients (Bellevue à la place de Redmond). Pour modifier le nom de ville, vous devez fournir un **où** attribut de propriété qui identifie les trois membres dans le client pour lequel les membres de l’attribut Ville doivent être changés. Si vous ne fournissez pas cette **où** propriété, tous les clients dont le nom ville actuel est Redmond aurait le nom de ville Bellevue après le **mise à jour** commande s’exécute.  
  
    > [!NOTE]  
    >  À l’exception des nouveaux membres, le **mettre à jour** commande peut uniquement mettre à jour les valeurs de clé d’attribut des attributs non inclus dans le **où** clause. Par exemple, le nom de ville ne peut pas être mis à jour lors de la mise à jour d'un client ; sinon, le nom de ville est modifié pour tous les clients.  
  
### <a name="updating-members-in-parent-attributes"></a>Mise à jour des membres d'attributs parents  
 Pour prendre en charge les attributs parents, le **mise à jour** commande facultatif [MoveWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/movewithdescendants-element-xmla)propriété. Définition de la **MoveWithDescendants** propriété la valeur true indique que les descendants du membre parent doivent également être déplacés avec le membre parent lorsque l’identificateur de ce membre parent est modifié. Si cette valeur est définie à false, le déplacement d'un membre parent entraîne la promotion des descendants immédiats de ce membre parent au niveau précédent du membre parent.  
  
 Lors de la mise à jour des membres dans un attribut parent, le **mettre à jour** commande ne peut pas mettre à jour les membres des autres attributs.  
  
## <a name="dropping-existing-members"></a>Suppression de membres existants  
 Avant de construire le **Drop** commande, vous devez disposer des informations suivantes pour les membres à supprimer :  
  
-   La dimension dans laquelle les membres existants doivent être supprimés.  
  
-   Les attributs de la dimension dans lesquels les membres existants doivent être supprimés.  
  
-   Les clés des membres existants à supprimer. Si un attribut utilise une clé composite, la clé peut nécessiter plusieurs valeurs.  
  
 Le **Drop** commande accepte uniquement deux propriétés requises :  
  
-   Le **objet** propriété, qui contient une référence d’objet pour la dimension dans lequel les membres doivent être supprimés. La référence d'objet contient l'identificateur de base de données, l'identificateur de cube et l'identificateur de la dimension.  
  
-   Le **où** propriété, qui contient un ou plusieurs **attribut** éléments pour limiter les attributs dans lequel les membres doivent être supprimées. Le **où** propriété est essentielle de limiter un **Drop** commande à des instances spécifiques d’un membre. Si le **où** commande n’est pas spécifiée, toutes les instances d’un membre donné sont supprimés. Par exemple, supposons que vous voulez supprimer tois clients de la ville de Redmond. Pour supprimer ces clients, vous devez fournir un **où** propriété qui identifie les trois membres de l’attribut Customer à supprimer et le membre Redmond de l’attribut City à partir de laquelle les trois clients doivent être supprimés. Si le **où** propriété spécifie uniquement le membre Redmond de l’attribut City, tous les clients associés à Redmond sont supprimés par le **Drop** commande. Si le **où** propriété spécifie uniquement les trois membres de l’attribut Customer, les trois clients seraient supprimés entièrement par le **Drop** commande.  
  
    > [!NOTE]  
    >  Le **attribut** éléments inclus dans un **Drop** commande doit contenir uniquement la **AttributeName** et **clés** propriétés. Sinon, une erreur risque de se produire.  
  
### <a name="dropping-members-in-parent-attributes"></a>Suppression de membres d'attributs parents  
 Définition de la [DeleteWithDescendants](https://docs.microsoft.com/bi-reference/xmla/xml-elements-properties/deletewithdescendants-element-xmla) propriété indique que les descendants d’un membre parent doivent également être supprimés avec le membre parent. Si cette valeur est définie à false, les descendants immédiats du membre parent sont alors promus au niveau antérieur du membre parent.  
  
> [!IMPORTANT]  
>  Un utilisateur n'a besoin que d'autorisations de suppression du membre parent pour pouvoir supprimer à la fois le membre parent et ses descendants. Il n'a pas besoin d'autorisations de suppression des descendants.  
  
## <a name="see-also"></a>Voir aussi  
 [Élément DROP &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/drop-element-xmla)   
 [Insérer un élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/insert-element-xmla)   
 [Mettre à jour d’élément &#40;XMLA&#41;](https://docs.microsoft.com/bi-reference/xmla/xml-elements-commands/update-element-xmla)   
 [Définition et identification d’objets &#40;XMLA&#41;](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/defining-and-identifying-objects-xmla.md)   
 [Développement avec XMLA dans Analysis Services](../../analysis-services/multidimensional-models-scripting-language-assl-xmla/developing-with-xmla-in-analysis-services.md)  
  
  
