---
title: Rechercher, méthode (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Find
- Recordset15::Find
helpviewer_keywords:
- Find method [ADO]
ms.assetid: 55c9810a-d8ca-46c2-a9dc-80e7ee7aa188
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: a3f544ae5a38b50ed13ddbafb725c07e0c8a4c8e
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66697956"
---
# <a name="find-method-ado"></a>Find, méthode (ADO)
Recherche un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) pour la ligne répondant aux critères spécifiés. Si vous le souhaitez, la direction de recherche, de ligne de début et de décalage à partir de la ligne initiale peut être spécifiée. Si les critères sont satisfaits, la position de ligne actuelle est définie sur l’enregistrement est trouvé ; Sinon, la position est définie à la fin (ou le début) de la **Recordset**.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
Find (Criteria, SkipRows, SearchDirection, Start)  
```  
  
#### <a name="parameters"></a>Paramètres  
 *Critères*  
 Un **chaîne** valeur qui contient une instruction en spécifiant le nom de colonne, un opérateur de comparaison et une valeur à utiliser dans la recherche.  
  
 *SkipRows*  
 Facultatif *.* Un **Long** valeur, dont la valeur par défaut est égale à zéro, ce qui spécifie l’offset de ligne à partir de la ligne actuelle ou *Démarrer* signet pour commencer la recherche. Par défaut, la recherche démarre sur la ligne actuelle.  
  
 *SearchDirection*  
 Facultatif *.* Un [SearchDirectionEnum](../../../ado/reference/ado-api/searchdirectionenum.md) valeur qui spécifie si la recherche doit commencer sur la ligne actuelle ou de la ligne suivante disponible dans la direction de la recherche. Une recherche s’arrête à la fin de la **Recordset** si la valeur est **adSearchForward**. Une recherche s’arrête au début de la **Recordset** si la valeur est **adSearchBackward**.  
  
 *Démarrer*  
 Facultatif. Un **Variant** signet qui indique la position de départ pour la recherche.  
  
## <a name="remarks"></a>Notes  
 Seul un nom de colonne unique peut être spécifié dans *critères*. Cette méthode ne prend pas en charge les recherches sur plusieurs colonnes.  
  
 L’opérateur de comparaison dans *critères* peut être « **>** « (supérieur à), » **\<** » (inférieur à), « = » (égal), « > = » (supérieur ou égal à), « < = » (inférieur ou égal à), « <> » (non égal), ou « like » (critères spéciaux).  
  
 La valeur dans *critères* peut être une chaîne, un nombre à virgule flottante ou une date. Valeurs de chaîne sont délimitées par des guillemets simples ou « # » (signe dièse) (par exemple, « état = 'WA' » ou « état = #WA # »). Valeurs de date sont séparés par des signes « # » (signe dièse) (par exemple, « start_date > #7/22/97 # »). Ces valeurs peuvent contenir des heures, minutes et secondes pour indiquer la date et heure indiquées, mais ne doivent pas contenir de millisecondes ou des erreurs se produisent.  
  
 Si l’opérateur de comparaison est « like », la valeur de chaîne peut contenir un astérisque (*) pour rechercher une ou plusieurs occurrences de n’importe quel caractère ou une sous-chaîne. Par exemple, « state like'm\*' » correspond à Maine et du Massachusetts. Vous pouvez également utiliser des astérisques de début et de fin pour rechercher une sous-chaîne contenue dans les valeurs. Par exemple, « état comme '\*comme\*' » correspond à Alaska, Arkansas et Massachusetts.  
  
 Astérisques peuvent être utilisés uniquement à la fin d’une chaîne de critères ou au début et à la fin d’une chaîne de critères, comme indiqué ci-dessus. Vous ne pouvez pas utiliser l’astérisque comme caractère générique de début ('* str'), ou comme un s embedded\*r »). Cela entraîne une erreur.  
  
> [!NOTE]
>  Une erreur se produit si une position de ligne actuelle n’est pas définie avant d’appeler **trouver**. Toute méthode qui définit la position de ligne, tel que [MoveFirst](../../../ado/reference/ado-api/movefirst-movelast-movenext-and-moveprevious-methods-ado.md), doit être appelée avant d’appeler **trouver**.  
  
> [!NOTE]
>  Si vous appelez le **trouver** méthode sur un jeu d’enregistrements et la position actuelle dans le jeu d’enregistrements est au dernier enregistrement ou à la fin du fichier (EOF), vous ne trouverez pas quoi que ce soit. Vous devez appeler la **MoveFirst** méthode pour définir la position/le curseur actuel au début de l’ensemble d’enregistrements.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Rechercher l’exemple de méthode (VB)](../../../ado/reference/ado-api/find-method-example-vb.md)   
 [Propriété index](../../../ado/reference/ado-api/index-property.md)   
 [Optimize, propriété dynamique (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [Seek, méthode](../../../ado/reference/ado-api/seek-method.md)
