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
manager: craigg
ms.openlocfilehash: 2267ff0af67682417b118e9fa01b2dceeb1454a8
ms.sourcegitcommit: f7fced330b64d6616aeb8766747295807c92dd41
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63161434"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Émission de commandes vers le fournisseur de données sous-jacent
Les commandes qui ne commencent pas par une forme sont passé au fournisseur de données. Cela équivaut à l’émission d’une commande de la forme sous la forme « Forme {commande du fournisseur} ». Ces commandes n’ont *pas* ont produire un **Recordset**. Par exemple, « SHAPE {DROP TABLE MyTable} est une commande de la forme parfaitement valide, en supposant que le fournisseur de données prend en charge de DROP TABLE.  
  
 Cette fonctionnalité permet des commandes de fournisseur normales et les commandes shape pour partager la même connexion et la même transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de la mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
