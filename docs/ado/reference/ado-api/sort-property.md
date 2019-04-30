---
title: Trier de propriété | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::get_Sort
- Recordset15::put_Sort
- Recordset15::PutSort
- Recordset15::GetSort
- Recordset15::Sort
helpviewer_keywords:
- DESC [ADO]
- ASC [ADO]
- Sort property [ADO]
ms.assetid: 3683ffa0-6f93-4906-9533-ef6942f24f39
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 6c579c824d65d50dfd1b222615f247d97209db37
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63314679"
---
# <a name="sort-property"></a>Sort, propriété
Indique un ou plusieurs noms de champ sur lequel le [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) est triée, et indique si chaque champ est trié dans l’ordre croissant ou décroissant.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **chaîne** valeur qui indique le champ de noms dans le **Recordset** sur laquelle trier. Chaque nom est séparé par une virgule et éventuellement suivie d’une valeur vide et le mot clé, **ASC**, qui trie le champ dans l’ordre croissant, ou **DESC**, qui trie le champ dans l’ordre décroissant. Par défaut, si aucun mot clé n’est spécifié, le champ est trié dans l’ordre croissant.  
  
## <a name="remarks"></a>Notes  
 Cette propriété nécessite la [CursorLocation](../../../ado/reference/ado-api/cursorlocation-property-ado.md) propriété être définie sur **adUseClient**. Un index temporaire est créé pour chaque champ dans le **tri** propriété si un index n’existe pas déjà.  
  
 L’opération de tri est efficace, car les données ne sont pas réorganisées physiquement, mais simplement accédées dans l’ordre spécifié par l’index.  
  
 Lorsque la valeur de la **tri** propriété n’est pas une chaîne vide, le **tri** ordre de la propriété est prioritaire sur l’ordre spécifié dans un **ORDER BY** clause inclus dans l’instruction SQL utilisée pour ouvrir le **Recordset**.  
  
 Le **Recordset** ne doivent pas être ouverts avant d’accéder à la **tri** propriété ; elle peut être définie à tout moment après le **Recordset** objet est instancié.  
  
 Définition de la **tri** propriété sur une chaîne vide sera réinitialise les lignes dans leur ordre d’origine et supprimer des index temporaires. Les index existants ne seront pas supprimés.  
  
 Supposons qu’un **Recordset** contient trois champs nommés *firstName*, *middleInitial*, et *lastName*. Définir le **tri** à la chaîne de la propriété «`lastName DESC, firstName ASC`», ordre dans lequel sera le **Recordset** par nom de famille dans l’ordre décroissant, puis par prénom par ordre croissant. L’initiale du milieu est ignoré.  
  
 Aucun champ ne peut être nommé « ASC » ou « DESC », car ces noms en conflit avec les mots clés **ASC** et **DESC**. Vous pouvez créer un alias pour un champ avec un nom en conflit à l’aide de la **AS** mot clé dans la requête qui retourne le **Recordset**.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Sort, exemple de propriété (VB)](../../../ado/reference/ado-api/sort-property-example-vb.md)   
 [Sort, exemple de propriété (VC ++)](../../../ado/reference/ado-api/sort-property-example-vc.md)   
 [Optimize, propriété dynamique (ADO)](../../../ado/reference/ado-api/optimize-property-dynamic-ado.md)   
 [SortColumn, propriété (RDS)](../../../ado/reference/rds-api/sortcolumn-property-rds.md)   
 [SortDirection, propriété (RDS)](../../../ado/reference/rds-api/sortdirection-property-rds.md)
