---
title: Émettre des commandes vers le fournisseur de données sous-jacent | Microsoft Docs
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
author: MightyPen
ms.author: genemi
manager: jroth
ms.openlocfilehash: 231d9ced5bf370b8ee7c507e930e6961cfbed5a8
ms.sourcegitcommit: 074d44994b6e84fe4552ad4843d2ce0882b92871
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2019
ms.locfileid: "66700578"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Émission de commandes vers le fournisseur de données sous-jacent
Les commandes qui ne commencent pas par une forme sont passé au fournisseur de données. Cela équivaut à l’émission d’une commande de la forme sous la forme « Forme {commande du fournisseur} ». Ces commandes n’ont *pas* ont produire un **Recordset**. Par exemple, « SHAPE {DROP TABLE MyTable} est une commande de la forme parfaitement valide, en supposant que le fournisseur de données prend en charge de DROP TABLE.  
  
 Cette fonctionnalité permet des commandes de fournisseur normales et les commandes shape pour partager la même connexion et la même transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
