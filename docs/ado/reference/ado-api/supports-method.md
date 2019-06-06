---
title: Prend en charge de la méthode | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
apitype: COM
f1_keywords:
- Recordset15::raw_Supports
- Recordset15::Supports
helpviewer_keywords:
- Supports method [ADO]
ms.assetid: 298fc41c-0b55-42fc-b373-c5133b4da6a5
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 1d1df1d780cf9e1e631f6b146e45cc0a34da9438
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66710683"
---
# <a name="supports-method"></a>Supports, méthode
Détermine si une certaine [Recordset](../../../ado/reference/ado-api/recordset-object-ado.md) objet prend en charge un type particulier de fonctionnalité.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="return-value"></a>Valeur de retour  
 Retourne un **booléenne** valeur qui indique si toutes les fonctionnalités identifié par le *CursorOptions* argument sont pris en charge par le fournisseur.  
  
#### <a name="parameters"></a>Paramètres  
 *CursorOptions*  
 Un **Long** expression qui est constituée d’une ou plusieurs [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md) valeurs.  
  
## <a name="remarks"></a>Notes  
 Utilisez le **prend en charge** méthode pour déterminer les types de fonctionnalités un **Recordset** prend en charge de l’objet. Si le **Recordset** objet prend en charge les fonctionnalités dont les constantes correspondantes se trouvent dans *CursorOptions*, le **prend en charge** méthode retourne **True**. Sinon, elle retourne **False**.  
  
> [!NOTE]
>  Bien que le **prend en charge** méthode peut retourner **True** pour une fonctionnalité donnée, il ne pas garantit que le fournisseur peut proposer la fonctionnalité en toutes circonstances. Le **prend en charge** méthode renvoie simplement si le fournisseur peut prendre en charge la fonctionnalité spécifiée, sous réserve que certaines conditions sont remplies. Par exemple, le **prend en charge** méthode peut indiquer qu’un **Recordset** objet prend en charge les mises à jour même si le curseur est basé sur une jointure de plusieurs tables, dont certaines colonnes ne sont pas modifiables.  
  
## <a name="applies-to"></a>S'applique à  
 [Recordset, objet (ADO)](../../../ado/reference/ado-api/recordset-object-ado.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Prend en charge de l’exemple de méthode (VB)](../../../ado/reference/ado-api/supports-method-example-vb.md)   
 [Prend en charge de l’exemple de méthode (VC ++)](../../../ado/reference/ado-api/supports-method-example-vc.md)   
 [CursorType, propriété (ADO)](../../../ado/reference/ado-api/cursortype-property-ado.md)
