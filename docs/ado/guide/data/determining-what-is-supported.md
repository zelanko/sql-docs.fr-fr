---
title: Déterminer ce qui est pris en charge | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- editing data [ADO], Supports method
- Supports method [ADO]
ms.assetid: 65090cba-6d46-4775-8d61-f6838e7752a6
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: c6af51d8d69f5897021733468ee93290e1b5e280
ms.sourcegitcommit: 3026c22b7fba19059a769ea5f367c4f51efaf286
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2019
ms.locfileid: "66702096"
---
# <a name="determining-what-is-supported"></a>Détermination de ce qui est pris en charge
Le **prend en charge** méthode est utilisée pour déterminer si une certaine **Recordset** objet prend en charge un type particulier de fonctionnalité. Il présente la syntaxe suivante :  
  
```  
  
boolean = recordset.Supports(CursorOptions )  
```  
  
## <a name="remarks"></a>Notes  
 Le **prend en charge** méthode retourne une valeur booléenne qui indique si le fournisseur prend en charge toutes les fonctionnalités identifiées par l’argument CursorOptions. Vous pouvez utiliser la **prend en charge** méthode pour déterminer les types de fonctionnalités un **Recordset** prend en charge de l’objet. Si le **Recordset** objet prend en charge les fonctionnalités dont les constantes correspondantes se trouvent dans *CursorOptions*, le **prend en charge** méthode retourne **True**. Sinon, elle retourne **False**.  
  
 À l’aide de la **prend en charge** (méthode), vous pouvez vérifier la capacité de la **Recordset** objet à ajouter de nouveaux enregistrements, utiliser des signets, utilisez la **trouver** (méthode), utilisez le défilement, utilisez le  **Index** propriété et d’effectuer des mises à jour par lots. Pour obtenir une liste complète des constantes et leurs significations, consultez [CursorOptionEnum](../../../ado/reference/ado-api/cursoroptionenum.md).  
  
 Bien que le **prend en charge** méthode peut retourner **True** pour une fonctionnalité donnée, il ne pas garantit que le fournisseur peut proposer la fonctionnalité en toutes circonstances. Le **prend en charge** méthode renvoie simplement si le fournisseur peut prendre en charge la fonctionnalité spécifiée, sous réserve que certaines conditions sont remplies. Par exemple, le **prend en charge** méthode peut indiquer qu’un **Recordset** objet prend en charge les mises à jour, même si le curseur est basé sur une jointure de plusieurs tables - dont certaines colonnes ne sont pas modifiables.
