---
title: "Meilleures pratiques pour appeler des proc&#233;dures stock&#233;es compil&#233;es en mode natif | Microsoft Docs"
ms.custom: ""
ms.date: "03/24/2017"
ms.prod: "sql-server-2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "database-engine-imoltp"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: f39fc1c7-cfec-4a95-97f6-6b95954694bb
caps.latest.revision: 8
author: "JennieHubbard"
ms.author: "jhubbard"
manager: "jhubbard"
caps.handback.revision: 8
---
# Meilleures pratiques pour appeler des proc&#233;dures stock&#233;es compil&#233;es en mode natif
  Les procédures stockées compilées en mode natif sont les suivantes :  
  
-   utilisées en général dans les parties ayant un impact sur les performances d'une application ;  
  
-   exécutées fréquemment ;  
  
-   réputées très rapides.  
  
 L'avantage lié à l'utilisation d'une procédure stockée compilée en mode natif augmente avec le nombre de lignes et la quantité de logique qui est traitée par la procédure. Par exemple, une procédure stockée compilée en mode natif présentera de meilleures performances si elle utilise un ou plusieurs des éléments suivants :  
  
-   agrégation ;  
  
-   jointures de boucles imbriquées ;  
  
-   opérations de sélection, insertion, mise à jour et suppression en plusieurs instructions ;  
  
-   expressions complexes ;  
  
-   logique procédurale, par exemple des instructions conditionnelles et des boucles.  
  
 Si vous devez traiter une seule ligne, l'utilisation d'une procédure stockée compilée en mode natif peut ne pas fournir un avantage en matière de performances.  
  
 Pour éviter que le serveur soit contraint de mettre en correspondance les noms des paramètres et les types de conversion :  
  
-   Faites correspondre les types de paramètres transmis à la procédure avec les types dans la définition de la procédure.  
  
-   Utilisez des paramètres (sans nom) ordinaux lorsque vous appelez des procédures stockées compilées en mode natif. Pour une exécution optimale, n'utilisez pas de paramètres nommés.  
  
 L’utilisation de paramètres nommés (inefficaces) avec des procédures stockées compilées en mode natif peut être détectée par le XEvent **hekaton_slow_parameter_passing**, avec **reason=named_parameters**.  
  
 De même, vous pouvez détecter l’utilisation de types incompatibles dans le même XEvent **hekaton_slow_parameter_passing**, avec **reason=parameter_conversion**.  
  
 Étant donné que vous devez implémenter la logique de nouvelle tentative lors de l'utilisation des tables mémoire optimisées (dans de nombreux scénarios), et que vous devrez contourner certaines limitations de fonctionnalités, vous pouvez créer une procédure stockée [!INCLUDE[tsql](../../includes/tsql-md.md)] interprétée par wrapper. Pour obtenir un exemple, consultez [Transactions with Memory-Optimized Tables](../../relational-databases/in-memory-oltp/transactions-with-memory-optimized-tables.md) (Transactions avec des tables optimisées en mémoire).  
  
## Voir aussi  
 [Procédures stockées compilées en mode natif](../../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md)  
  
  