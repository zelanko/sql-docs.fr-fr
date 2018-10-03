---
title: Bookmark, propriété (ADO) | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 03/20/2018
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::Bookmark
helpviewer_keywords:
- Bookmark property [ADO]
ms.assetid: 481dcc93-487b-490e-ac58-a1e9b2ebfd43
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 61fa4619bd70b170f13dbc879748364f019f8bdd
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47716297"
---
# <a name="bookmark-property-ado"></a>Bookmark, propriété (ADO)
Indique un signet qui identifie de façon unique l’enregistrement actif dans un [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) de l’objet ou définit l’enregistrement actif un **Recordset** objet enregistrement identifié par un signet valide.  
  
## <a name="settings-and-return-values"></a>Paramètres et valeurs de retour  
 Définit ou retourne un **Variant** expression qui correspond à un signet valid.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **signet** propriété pour enregistrer la position de l’enregistrement actif et revenir à cet enregistrement à tout moment. Les signets sont disponibles uniquement dans **Recordset** objets prenant en charge la fonctionnalité de signet.  
  
 Lorsque vous ouvrez un **Recordset** de l’objet, chacun de ses enregistrements possède un signet unique. Pour enregistrer le signet de l’enregistrement en cours, affectez la valeur de la **signet** propriété à une variable. Pour retourner rapidement à cet enregistrement à tout moment après avoir déplacé vers un autre enregistrement, définissez la **Recordset** l’objet **signet** propriété à la valeur de cette variable.  
  
 L’utilisateur ne peut pas être en mesure d’afficher la valeur du signet. En outre, les utilisateurs ne devraient pas les signets soient directement comparables, étant donné que les deux signets qui font référence au même enregistrement peuvent avoir des valeurs différentes.  
  
 Si vous utilisez le [Clone](../../../ado/reference/ado-api/clone-method-ado.md) méthode pour créer une copie d’un **Recordset** objet, le **signet** paramètres de propriété pour la version d’origine et le doublon **Recordset**  objets sont identiques et vous pouvez les utiliser indifféremment. Toutefois, vous ne pouvez pas utiliser des signets à partir de différents **Recordset** objets de manière interchangeable, même si elles ont été créées à partir de la même source ou commande.  
  
> [!NOTE]
>  **Utilisation de Service de données à distance** lorsqu’il est utilisé sur une côté client **Recordset** objet, le **signet** propriété est toujours disponible.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [BOF, EOF et Bookmark, exemple de propriétés (VB)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vb.md)   
 [BOF, EOF et Bookmark, propriétés-exemple (VC ++)](../../../ado/reference/ado-api/bof-eof-and-bookmark-properties-example-vc.md)   
 [Supports, méthode](../../../ado/reference/ado-api/supports-method.md)
