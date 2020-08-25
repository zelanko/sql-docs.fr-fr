---
description: Émission de commandes vers le fournisseur de données sous-jacent
title: Émission de commandes vers le Fournisseur de données sous-jacent | Microsoft Docs
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
author: rothja
ms.author: jroth
ms.openlocfilehash: 290ec3a535ac7fe4672f8d0ab6ea19e4d4997333
ms.sourcegitcommit: 33e774fbf48a432485c601541840905c21f613a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88805879"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Émission de commandes vers le fournisseur de données sous-jacent
Toute commande qui ne commence pas par SHAPE est transmise au fournisseur de données. Cela équivaut à émettre une commande de forme sous la forme « SHAPE {Provider Command} ». Il n’est *pas* nécessaire que ces commandes produisent un **jeu d’enregistrements**. Par exemple, «la forme {DROP TABLE MyTable} est une commande de forme parfaitement valide, en supposant que le fournisseur de données prend en charge DROP TABLE.  
  
 Cette fonctionnalité permet aux commandes de fournisseur normales et aux commandes de forme de partager la même connexion et la même transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](./data-shaping-example.md)   
 [Grammaire de forme formelle](./formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](./shape-commands-in-general.md)