---
title: Plusieurs Transactions | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: conceptual
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
caps.latest.revision: 31
author: douglaslms
ms.author: douglasl
manager: craigg
ms.openlocfilehash: aa4e3015365166fc827170f021292a65d5d52dc7
ms.sourcegitcommit: c18fadce27f330e1d4f36549414e5c84ba2f46c2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/02/2018
ms.locfileid: "37219509"
---
# <a name="multiple-transactions"></a>Transactions multiples
  Il est possible qu'un package inclue des transactions non liées entre elles dans un package [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)]. Chaque fois qu'un conteneur, au milieu d'une hiérarchie de conteneurs imbriquée, ne prend pas en charge les transactions, les conteneurs au-dessus et au-dessous de lui dans la hiérarchie démarrent des transactions distinctes s'ils sont configurés pour prendre en charge les transactions. Les transactions sont validées ou annulées dans l'ordre, de la tâche la plus imbriquée dans la hiérarchie de conteneurs jusqu'au package. Cependant, si une transaction interne est validée, elle n'est pas annulée si une transaction externe est abandonnée.  
  
## <a name="illustration-of-multiple-transactions"></a>Illustration de plusieurs transactions  
 Par exemple, un package comprend un conteneur de séquences qui contient deux conteneurs de boucles Foreach, et chaque conteneur comprend deux tâches d'exécution de requêtes SQL. Le conteneur de séquences et les tâches d'exécution de requêtes SQL prennent en charge les transactions, contrairement aux conteneurs de boucles Foreach. Dans cet exemple, chaque tâche d'exécution de requêtes SQL démarre sa propre transaction et elle n'est pas annulée si la transaction de la tâche de séquence est abandonnée.  
  
 Les propriétés TransactionOption du conteneur de séquences, du conteneur de boucle Foreach et des tâches d’exécution de requêtes SQL sont définies comme suit :  
  
-   La propriété TransactionOption du conteneur de séquences a pour valeur **Required**.  
  
-   Les propriétés TransactionOption des conteneurs de boucles Foreach ont pour valeur **NotSupported**.  
  
-   Les propriétés TransactionOption des tâches d’exécution de requêtes SQL ont pour valeur **Required**.  
  
 Le diagramme ci-dessous représente les cinq transactions non liées du package. Une transaction est démarrée par le conteneur de séquences et quatre transactions par les tâches d'exécution SQL.  
  
 ![Implémentation de plusieurs transactions](media/mw-dts-trans2.gif "Implémentation de plusieurs transactions")  
  
## <a name="related-tasks"></a>Related Tasks  
 [Configurer un package pour l’utilisation de transactions](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  
