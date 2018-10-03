---
title: Limites d’un Recordset | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- EOF property [ADO], boundaries of a Recordset
- Recordset object [ADO], boundaries of a Recordset
- BOF property [ADO], boundaries of a Recordset
ms.assetid: c0dd4a0f-478d-4c5e-b5d5-7535f211d064
author: MightyPen
ms.author: genemi
manager: craigg
ms.openlocfilehash: 4c9e05a45b5f035a500e210c991a33216be318ea
ms.sourcegitcommit: 61381ef939415fe019285def9450d7583df1fed0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/01/2018
ms.locfileid: "47633447"
---
# <a name="boundaries-of-a-recordset"></a>Limites d’un recordset
**Jeu d’enregistrements** prend en charge la **BOF** et **EOF** propriétés pour délimiter le début et la fin, respectivement, du jeu de données. Vous pouvez considérer **BOF** et **EOF** sous forme d’enregistrements « fantômes » qui sont placés au début et à la fin de la **Recordset**. Comptage **BOF** et **EOF**, notre exemple **Recordset** ressemblerait maintenant à ceci :  
  
|ProductID|ProductName|UnitPrice|  
|---------------|-----------------|---------------|  
|BOF|||  
|7|Poires secs organiques d’oncle Bob|30.0000|  
|14|Tofu|23.2500|  
|28|Rssle choucroute|45.6000|  
|51|Manjimup pommes en poudre|53.0000|  
|74|Longlife Tofu|10.0000|  
|EOF|||  
  
 Lorsqu’un curseur se déplace au-delà du dernier enregistrement, **EOF** a la valeur **True**; sinon, sa valeur est **False**. De même, lorsque le curseur se place avant le premier enregistrement, **BOF** a la valeur **True**; sinon, sa valeur est **False**. Ces propriétés sont couramment utilisées pour énumérer les enregistrements dans le jeu de données, comme illustré dans le fragment de code JScript suivant.  
  
```  
while (objRecordset.EOF != true)   
{  
   // Work on the current record.  
   ...  
   // Advance the cursor forward to the next record.  
   objRecordset.MoveNext();  
}  
or  
while (objRecordset.BOF != true)   
{  
   // Work on the current record.  
   ...  
   // Move the cursor to the previous record.  
   objRecordset.MovePrevious();  
}  
```  
  
 Si les deux **BOF** et **EOF** sont **True**, le **Recordset** objet est vide. Les deux propriétés seront **False** pour récemment ouverte, non vides **Recordset** objet. Vous pouvez utiliser la **BOF** et **EOF** propriétés afin de déterminer si un **Recordset** objet est vide ou non, comme dans le fragment de code JScript suivant.  
  
```  
if (objRecordset.EOF == true && objRecordset.BOF == true)  
{  
   WScript.Echo("we got an empty dataset.");  
}  
else  
{  
   WScript.Echo("we got a full dataset.");  
}  
```  
  
 Ce schéma fonctionne pour tous les types de curseur et est indépendant des fournisseurs sous-jacents. Si vous essayez de déterminer la vérifier d’un **Recordset** objet en vérifiant si sa **RecordCount** valeur de propriété est zéro (0) ou non, vous devez prendre des précautions pour utiliser un curseur approprié et le fournisseur qui prend en charge le retour du nombre d’enregistrements dans le résultat.  
  
 Si vous supprimez le dernier enregistrement restant dans le **Recordset** de l’objet, le curseur se trouve dans un état indéterminé. Le **BOF** et **EOF** propriétés peuvent rester **False** jusqu'à ce que vous tentiez de repositionner l’enregistrement en cours, en fonction du fournisseur. Pour plus d’informations, consultez [les enregistrements de suppression à l’aide de la méthode Delete](../../../ado/guide/data/deleting-records-using-the-delete-method.md).
