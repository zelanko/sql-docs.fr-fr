---
title: Émet des commandes pour le fournisseur de données sous-jacent | Documents Microsoft
ms.prod: sql
ms.prod_service: drivers
ms.service: ''
ms.component: ado
ms.technology:
- drivers
ms.custom: ''
ms.date: 01/19/2017
ms.reviewer: ''
ms.suite: sql
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- shape commands [ADO]
- underlying providers [ADO]
- data shaping [ADO], commands
ms.assetid: d6001863-7733-4c32-817f-081e48587fa1
caps.latest.revision: 10
author: MightyPen
ms.author: genemi
manager: craigg
ms.workload: Inactive
ms.openlocfilehash: 30734d534d1ac8e82bfb064570c130d3547c8cc4
ms.sourcegitcommit: bb044a48a6af9b9d8edb178dc8c8bd5658b9ff68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/18/2018
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Émet des commandes pour le fournisseur de données sous-jacent
Les commandes qui ne commencent pas par une forme sont passé au fournisseur de données. Cela équivaut à émettre une commande de la forme sous la forme « SHAPE {commande du fournisseur} ». Ces commandes ne *pas* ont produire un **Recordset**. Par exemple, « forme {DROP TABLE MyTable} est une commande de la forme parfaitement valide, si que le fournisseur de données prend en charge de DROP TABLE.  
  
 Cette fonctionnalité permet des commandes de fournisseur normales et des commandes de forme de partager la même connexion et la même transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de mise en forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
