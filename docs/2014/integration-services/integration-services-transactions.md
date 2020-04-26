---
title: Transactions Integration Services | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: integration-services
ms.topic: conceptual
helpviewer_keywords:
- containers [Integration Services], transactions
- transactions [Integration Services], about transactions in packages
- tasks [Integration Services], transactions
- transactions [Integration Services]
ms.assetid: 3c78bb26-ddce-4831-a5f8-09d4f4fd53cc
author: janinezhang
ms.author: janinez
manager: craigg
ms.openlocfilehash: b0359ca10e7279f4a80bec082a8e049f4641c9b2
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/25/2020
ms.locfileid: "62767631"
---
# <a name="integration-services-transactions"></a>Transactions Integration Services
  Les packages utilisent les transactions pour lier les actions de base de données que les tâches effectuent en unités atomiques, et maintiennent ce faisant l'intégrité des données. Tous les types de conteneurs [!INCLUDE[msCoName](../includes/msconame-md.md)] [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] (packages, conteneurs de boucles For et Foreach et conteneurs de séquences, ainsi que les hôtes de tâches qui encapsulent chaque tâche) peuvent être configurés pour utiliser les transactions. [!INCLUDE[ssISnoversion](../includes/ssisnoversion-md.md)] offre trois options de configuration des transactions : **NotSupported**, **Supported**et **Required**.  
  
-   **Required** indique que le conteneur démarre une transaction, à moins qu’une autre transaction soit déjà démarrée par son conteneur parent. Si la transaction existe déjà, le conteneur rejoint la transaction. Par exemple, si un package non configuré pour prendre en charge les transactions inclut un conteneur de séquences utilisant l’option **Required** , le conteneur de séquences démarre sa propre transaction. Si le package a été configuré pour utiliser l’option **Required** , le conteneur de séquences rejoint la transaction du package.  
  
-   **Supported** indique que le conteneur ne démarre pas de transaction, mais rejoint toute transaction démarrée par son conteneur parent. Par exemple, si un package avec quatre tâches d’exécution SQL démarre une transaction et que les quatre tâches utilisent l’option **Supported** , les mises à jour de la base de données effectuées par les tâches d’exécution SQL sont annulées en cas d’échec d’une des tâches. Si le package ne démarre pas de transaction, les quatre tâches d'exécution SQL ne sont pas liées par une transaction et aucune mise à jour de la base de données n'est annulée, sauf celle effectuée par la tâche qui a échoué.  
  
-   **NotSupported** indique que le conteneur ne démarre pas de transaction et ne rejoint aucune transaction existante. Une transaction démarrée par un conteneur parent n'affecte pas les conteneurs enfants configurés pour ne pas prendre en charge les transactions. Par exemple, si un package est configuré pour démarrer une transaction et qu’un conteneur de boucles For dans le package utilise l’option **NotSupported** , aucune des tâches de la boucle For ne peut être annulée si elle échoue.  
  
 Vous pouvez configurer les transactions en définissant la propriété TransactionOption sur le conteneur. Vous pouvez définir cette propriété dans la fenêtre **Propriétés** de [!INCLUDE[ssBIDevStudioFull](../includes/ssbidevstudiofull-md.md)]ou par programmation.  
  
> [!NOTE]  
>  La propriété `TransactionOption` a un impact sur la décision d'appliquer ou non la valeur de la propriété `IsolationLevel` demandée par un conteneur. Pour plus d’informations, consultez la description de `IsolationLevel` la propriété dans la rubrique [définition des propriétés](set-package-properties.md)d’un package.  
  
### <a name="to-configure-a-package-to-use-transactions"></a>Pour configurer un package pour l'utilisation de transactions  
  
-   [Configurer un package pour l'utilisation de transactions](../relational-databases/native-client-ole-db-transactions/transactions.md)  
  
## <a name="external-resources"></a>Ressources externes  
  
-   Entrée de blog, [How to Use Transactions in SQL Server Integration Services SSIS](https://go.microsoft.com/fwlink/?LinkId=157783)(Comment utiliser des transactions dans SQL Server Integration Services SSIS), sur www.mssqltips.com  
  
## <a name="see-also"></a>Voir aussi  
 [Transactions héritées](../../2014/integration-services/inherited-transactions.md)   
 [Transactions multiples](../../2014/integration-services/multiple-transactions.md)  
  
  
