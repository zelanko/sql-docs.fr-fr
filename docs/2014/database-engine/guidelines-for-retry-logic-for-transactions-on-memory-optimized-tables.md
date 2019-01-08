---
title: Instructions pour la logique de nouvelle tentative pour les Transactions sur les Tables mémoire optimisées | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: f2a35c37-4449-49ee-8bba-928028f1de66
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 4f4c4244b2d4c9bd785202805312f64194c73b5b
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52531667"
---
# <a name="guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables"></a>Instructions pour la logique de nouvelle tentative des transactions sur des tables mémoire optimisées
  Certaines conditions d'erreur peuvent se produire lors de l'accès des transactions aux tables mémoire optimisées.  
  
-   41302. La transaction en cours a tenté de mettre à jour un enregistrement lui-même mis à jour depuis le démarrage de la transaction.  
  
-   41305. La transaction en cours n'a pas été validée en raison d'un échec de validation REPEATABLE READ.  
  
-   41325. La transaction en cours n'a pas été validée en raison d'un échec de validation SERIALIZABLE.  
  
-   41301. Une transaction précédente à la transaction actuelle a pris une dépendance ou a été abandonnée, et la transaction en cours ne peut plus être validée.  
  
 Ces erreurs sont souvent dues à une interférence entre des transactions exécutées simultanément. L'action corrective habituelle consiste à réessayer la transaction.  
  
 Pour plus d’informations sur ces conditions d’erreur, consultez la section sur la détection de conflit, Validation et contrôles de dépendance de validation dans [Transactions dans les Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Les blocages (code d'erreur 1205) ne peuvent pas se produire pour les tables mémoire optimisées, car celles-ci n'utilisent pas de verrous. Toutefois, si l'application contient déjà une logique de nouvelle tentative pour les blocages, la logique existante peut être étendue pour inclure les nouveaux codes d'erreur.  
  
## <a name="considerations-for-retrying"></a>Considérations relatives à la logique de nouvelle tentative  
 Les applications rencontreront généralement des conflits entre les transactions et devront implémenter une logique de nouvelle tentative pour les résoudre. Le nombre des conflits rencontrés dépend de plusieurs facteurs :  
  
-   Contention de lignes individuelles. Plus le nombre de transactions tentant de mettre à jour la même ligne est élevé, plus le risque de conflits augmente.  
  
-   Nombre de lignes lues par les transactions REPEATABLE READ. Plus le nombre de lignes lues est important, plus il est probable que certaines de ces lignes soient mises à jour par des transactions simultanées. Cela génère des échecs de validation REPEATABLE READ.  
  
-   Taille des plages d'analyse utilisées par les transactions SERIALIZABLE. Plus les plages d'analyse sont grandes, plus il est probable que des transactions simultanées génèrent des lignes fantômes, provoquant des échecs de validation SERIALIZABLE.  
  
     Une application peut difficilement éviter ces conflits, qui nécessitent une logique de nouvelle tentative.  
  
> [!IMPORTANT]  
>  Les transactions en lecture-écriture qui accèdent aux tables mémoire optimisées requièrent une logique de nouvelle tentative.  
  
### <a name="considerations-for-read-only-transactions-and-natively-compiled-stored-procedures"></a>Considérations relatives aux transactions en lecture seule et aux procédures stockées compilées en mode natif  
 Les transactions en lecture seule qui couvrent une seule exécution d'une procédure stockée compilée en mode natif ne nécessitent pas de validation pour les transactions REPEATABLE READ et SERIALIZABLE. Les conflits d'écriture ne peuvent pas être dus à une transaction qui est en lecture seule.  
  
 Toutefois, des échecs de dépendance peuvent encore se produire. Les échecs de dépendance sont plus rares que les erreurs résultant des conflits. Par conséquent, dans la plupart des cas, une logique de nouvelle tentative spécifique n'est pas requise pour les transactions en lecture seule qui couvrent des exécutions uniques des procédures stockées compilées en mode natif.  
  
### <a name="considerations-for-read-only-transactions-and-cross-container-transactions"></a>Considérations relatives aux transactions en lecture seule et aux transactions entre conteneurs  
 Les transactions en lecture seule entre conteneurs, qui sont des transactions démarrées en dehors du contexte d'une procédure stockée compilée en mode natif, n'effectuent pas de validation si toutes les tables mémoire optimisées sont accessibles avec l'isolation SNAPSHOT. Toutefois, lorsque les tables mémoire optimisées sont accessibles avec l'isolation REPEATABLE READ ou SERIALIZABLE, la validation est exécutée au moment de la validation. Dans ce cas, la logique de nouvelle tentative peut être nécessaire.  
  
 Pour plus d’informations, consultez la section sur les Transactions entre conteneurs dans [niveaux d’Isolation des transactions](../../2014/database-engine/transaction-isolation-levels.md).  
  
## <a name="implementing-retry-logic"></a>Implémenter la logique de nouvelle tentative  
 Comme avec toutes les transactions qui ont accès aux tables mémoire optimisées, vous devez prendre en compte la logique de nouvelle tentative pour gérer les problèmes potentiels, tels que des conflits d'écriture (code d'erreur 41302) ou les problèmes de dépendance (code d'erreur 41301). Dans la plupart des applications le taux d'échec est bas, mais il est encore nécessaire de gérer les erreurs en effectuant une nouvelle tentative de transaction. Les deux méthodes suggérées pour implémenter la logique de nouvelle tentative sont les suivantes :  
  
-   Nouvelles tentatives côté client. Les nouvelles tentatives côté client constituent la méthode privilégiée pour implémenter la logique de nouvelle tentative en général. L'application cliente décèle l'erreur retournée par la transaction, et effectue une nouvelle tentative de transaction. Si une application cliente existante possède une logique de nouvelle tentative pour gérer les blocages, vous pouvez étendre l'application de façon à gérer les codes d'erreur.  
  
-   Utilisation d'une procédure stockée de wrapper. Le client appelle une procédure stockée en [!INCLUDE[tsql](../includes/tsql-md.md)] interprété qui appelle la procédure stockée compilée en mode natif ou exécute la transaction. La procédure de wrapper utilise ensuite la logique try/catch pour déceler l'erreur et effectuer une nouvelle tentative d'appel de procédure si nécessaire. Il est possible que le résultat soit retourné au client avant l'échec, et le client ne peut pas l'ignorer. Par conséquent, il est préférable d'utiliser cette méthode uniquement avec des procédures stockées compilées en mode natif qui ne retournent aucun jeu de résultats au client.  
  
 La logique de nouvelle tentative peut être implémentée en [!INCLUDE[tsql](../includes/tsql-md.md)] ou dans le code de l'application dans la couche intermédiaire.  
  
 Voici deux raisons pour prendre en considération la logique de nouvelle tentative :  
  
-   L'application cliente applique la logique de nouvelle tentative pour d'autres codes d'erreur, comme 1205, que vous pouvez étendre.  
  
-   Les conflits sont rares, mais il est important de réduire la latence de bout en bout à l'aide d'une exécution préparée. Pour plus d’informations sur l’exécution en mode natif directement les procédures stockées compilées, consultez [Natively Compiled Stored Procedures](../relational-databases/in-memory-oltp/natively-compiled-stored-procedures.md).  
  
 L'exemple suivant illustre la logique de nouvelle tentative dans une procédure stockée en [!INCLUDE[tsql](../includes/tsql-md.md)] interprété qui contient un appel à une procédure stockée compilée en mode natif ou à une transaction entre conteneurs.  
  
```tsql  
CREATE PROCEDURE usp_my_procedure @param1 type1, @param2 type2, ...  
AS  
BEGIN  
  -- number of retries - tune based on the workload  
  DECLARE @retry INT = 10  
  
  WHILE (@retry > 0)  
  BEGIN  
    BEGIN TRY  
  
      -- exec usp_my_native_proc @param1, @param2, ...  
  
      --       or  
  
      -- BEGIN TRANSACTION  
      --   ...  
      -- COMMIT TRANSACTION  
  
      SET @retry = 0  
    END TRY  
    BEGIN CATCH  
      SET @retry -= 1  
  
      -- the error number for deadlocks (1205) does not need to be included for   
      -- transactions that do not access disk-based tables  
      IF (@retry > 0 AND error_number() in (41302, 41305, 41325, 41301, 1205))  
      BEGIN  
        -- these error conditions are transaction dooming - rollback the transaction  
        -- this is not needed if the transaction spans a single native proc execution  
        --   as the native proc will simply rollback when an error is thrown   
        IF XACT_STATE() = -1  
          ROLLBACK TRANSACTION  
  
        -- use a delay if there is a high rate of write conflicts (41302)  
        --   length of delay should depend on the typical duration of conflicting transactions  
        -- WAITFOR DELAY '00:00:00.001'  
      END  
      ELSE  
      BEGIN  
        -- insert custom error handling for other error conditions here  
  
        -- throw if this is not a qualifying error condition  
        ;THROW  
      END  
    END CATCH  
  END  
END  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transactions sur les Tables optimisées en mémoire](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Transactions dans les Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md)   
 [Instructions pour les niveaux d’isolement des transactions sur les tables à mémoire optimisée](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)  
  
  
