---
title: Procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 06/13/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
helpviewer_keywords:
- natively compiled stored procedures
ms.assetid: d5ed432c-10c5-4e4f-883c-ef4d1fa32366
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: e9bdc0c104b212f3c26389c1792b6b617634a12a
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "62714916"
---
# <a name="natively-compiled-stored-procedures"></a>procédures stockées compilées en mode natif
  Les procédures stockées compilées en mode natif sont des procédures stockées [!INCLUDE[tsql](../../includes/tsql-md.md)] compilées en code natif qui accèdent aux tables optimisées en mémoire. Elles permettent une exécution efficace des requêtes et de la logique métier des procédures stockées. Pour plus d'informations sur le processus de compilation en mode natif, consultez [Native Compilation of Tables and Stored Procedures](native-compilation-of-tables-and-stored-procedures.md). Pour plus d’informations sur la migration des procédures stockées sur disque vers des procédures stockées compilées en mode natif, consultez [Problèmes de migration pour les procédures stockées compilées en mode natif](migration-issues-for-natively-compiled-stored-procedures.md).  
  
> [!NOTE]  
>  La différence entre les procédures stockées (sur disque) interprétées et les procédures stockées compilées en mode natif réside dans le fait qu'une procédure stockée interprétée est compilée lors de la première exécution, tandis qu'une procédure stockée compilée en mode natif l'est au moment de sa création. Avec des procédures stockées compilées en mode natif, de nombreuses conditions d'erreur (dépassement arithmétique, conversion de type, et certaines conditions de division par zéro) peuvent être détectées lors de la création et entraîner l'échec de la création de la procédure stockée compilée en mode natif. Avec des procédures stockées interprétées, ces conditions d'erreur ne provoquent généralement pas un échec lorsque la procédure stockée est créée, mais toutes les exécutions échoueront.  
  
 Rubriques de cette section :  
  
-   [Création de procédures stockées compilées en mode natif](creating-natively-compiled-stored-procedures.md)  
  
-   [Blocs Atomic](atomic-blocks-in-native-procedures.md)  
  
-   [Constructions prises en charge dans les procédures stockées compilées en mode natif](supported-features-for-natively-compiled-t-sql-modules.md)  
  
-   [Utilisation de Try..Catch dans des procédures stockées en mode natif](../../database-engine/using-try-catch-in-natively-compiled-stored-procedures.md)  
  
-   [Constructions prises en charge dans les procédures stockées compilées en mode natif](supported-ddl-for-natively-compiled-t-sql-modules.md)  
  
-   [Procédures stockées compilées en mode natif et options SET d'exécution](natively-compiled-stored-procedures-and-execution-set-options.md)  
  
-   [Meilleures pratiques pour appeler des procédures stockées compilées en mode natif](best-practices-for-calling-natively-compiled-stored-procedures.md)  
  
-   [Surveillance des performances des procédures stockées compilées en mode natif](monitoring-performance-of-natively-compiled-stored-procedures.md)  
  
-   [Appeler des procédures stockées compilées en mode natif à partir d'applications d'accès aux données](calling-natively-compiled-stored-procedures-from-data-access-applications.md)  
  
## <a name="see-also"></a>Voir aussi  
 [Tables optimisées en mémoire](memory-optimized-tables.md)  
  
  
