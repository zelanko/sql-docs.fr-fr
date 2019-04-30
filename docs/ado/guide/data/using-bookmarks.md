---
title: À l’aide de signets | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- bookmarks [ADO]
- Recordset object [ADO]
ms.assetid: cca244e6-84f8-4394-bca9-f7a819b8f4df
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: a083f9d411474769335fdfae32bd59dfe455a9f8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63184923"
---
# <a name="using-bookmarks"></a>Utilisation de signets
Il est souvent utile de retourner directement à un enregistrement spécifique après avoir déplacé dans le **Recordset** sans avoir à faire défiler tous les enregistrements et comparer des valeurs. Par exemple, si vous tentez de rechercher un enregistrement à l’aide de la **trouver** méthode mais la recherche ne renvoie aucun enregistrement, vous accédez automatiquement à chaque extrémité de la **Recordset**. Si votre fournisseur les prend en charge, les signets peuvent être utilisés pour marquer votre position avant d’utiliser le **trouver** méthode afin de pouvoir revenir à votre emplacement. Un signet est un **Variant** type valeur qui identifie de façon unique un enregistrement dans un **Recordset** objet.  
  
 Vous pouvez également utiliser un tableau de type variant de signets avec le **filtre de jeu d’enregistrements** méthode pour filtrer un jeu d’enregistrements sélectionné. Pour plus d’informations sur cette technique, consultez les résultats dans la rubrique, le filtrage [utilisation des Recordsets](../../../ado/guide/data/working-with-recordsets.md), plus loin dans cette section.  
  
 Vous pouvez utiliser la **signet** propriété pour obtenir un signet pour un enregistrement, ou définir l’enregistrement actif dans un **Recordset** objet enregistrement identifié par un signet valide. Le code suivant utilise la **signet** propriété pour définir un signet puis revenez à l’enregistrement de signet après avoir accédé à d’autres enregistrements. Pour déterminer si votre **Recordset** prend en charge les signets, utilisez la **prend en charge** (méthode).  
  
```  
'BeginBookmarkEg  
Dim varBookmark As Variant  
Dim blnCanBkmrk As Boolean  
  
objRs.Open strSQL, strConnStr, adOpenStatic, adLockOptimistic, adCmdText  
  
If objRs.RecordCount > 4 Then  
    objRs.Move 4                       ' move to the fifth record  
    blnCanBkmrk = objRs.Supports(adBookmark)  
    If blnCanBkmrk = True Then  
        varBookmark = objRs.Bookmark   ' record the bookmark  
        objRs.MoveLast                 ' move to a different record  
        objRs.Bookmark = varBookmark   ' return to the bookmarked (sixth) record  
    End If  
End If  
'EndBookmarkEg  
```  
  
 Le [prend en charge](../../../ado/reference/ado-api/supports-method.md) méthode est décrit plus en détail plus loin.  
  
 Sauf dans le cas de cloné **Recordsets**, les signets sont spécifiques à la **Recordset** dans lequel ils ont été créés, même si la même commande est utilisée. Cela signifie que vous ne pouvez pas utiliser un **signet** obtenu à partir d’un **Recordset** pour déplacer vers le même enregistrement dans une seconde **Recordset** ouvert avec la même commande.
