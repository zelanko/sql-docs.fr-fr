---
title: Plusieurs Transactions | Documents Microsoft
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology:
- integration-services
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- transactions [Integration Services], multiple
- multiple transactions
ms.assetid: c3664a94-be89-40c0-a3a0-84b74a7fedbe
caps.latest.revision: 31
author: douglaslMS
ms.author: douglasl
manager: jhubbard
ms.openlocfilehash: c98fa7454a1a01ee6879a514f369e6fb6c1a0570
ms.sourcegitcommit: 5dd5cad0c1bbd308471d6c885f516948ad67dfcf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2018
ms.locfileid: "36042542"
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
 [Configurer un Package pour utiliser des Transactions](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
  