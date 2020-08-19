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
ms.openlocfilehash: 6d9000fdf63a908257c9dbdfa29dc7b57dbb7ecf
ms.sourcegitcommit: e700497f962e4c2274df16d9e651059b42ff1a10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/17/2020
ms.locfileid: "88453231"
---
# <a name="issuing-commands-to-the-underlying-data-provider"></a>Émission de commandes vers le fournisseur de données sous-jacent
Toute commande qui ne commence pas par SHAPE est transmise au fournisseur de données. Cela équivaut à émettre une commande de forme sous la forme « SHAPE {Provider Command} ». Il n’est *pas* nécessaire que ces commandes produisent un **jeu d’enregistrements**. Par exemple, «la forme {DROP TABLE MyTable} est une commande de forme parfaitement valide, en supposant que le fournisseur de données prend en charge DROP TABLE.  
  
 Cette fonctionnalité permet aux commandes de fournisseur normales et aux commandes de forme de partager la même connexion et la même transaction.  
  
## <a name="see-also"></a>Voir aussi  
 [Exemple de mise en forme des données](../../../ado/guide/data/data-shaping-example.md)   
 [Grammaire de forme formelle](../../../ado/guide/data/formal-shape-grammar.md)   
 [Généralités sur les commandes SHAPE](../../../ado/guide/data/shape-commands-in-general.md)
