---
title: Transactions dans les tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 2cd07d26-a1f1-4034-8d6f-f196eed1b763
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: c953060e082ade1e325589cc712f723dabb4909d
ms.sourcegitcommit: e042272a38fb646df05152c676e5cbeae3f9cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2020
ms.locfileid: "78175406"
---
# <a name="transactions-in-memory-optimized-tables"></a>Transactions dans les tables mémoire optimisées
  Le contrôle de version de ligne des tables sur disque (à l'aide de l'isolation SNAPSHOT ou avec READ_COMMITTED_SNAPSHOT) fournit un type de contrôle d'accès concurrentiel optimiste. Les programmes d'écriture et les programmes de lecture ne se bloquent pas les uns les autres. Avec les tables mémoire optimisées, les programmes d'écriture ne bloquent pas les autres programmes d'écriture. Avec le contrôle de version de ligne pour les tables sur disque, une transaction verrouille la ligne et les transactions concomitantes tentant de mettre à jour cette ligne sont bloquées. Il n'existe pas de verrouillage avec les tables mémoire optimisées. En revanche, si deux transactions tentent de mettre à jour la même ligne, un conflit d'écriture/écriture (erreur 41302) se produit.

 Contrairement aux tables sur disque, les tables mémoire optimisées permettent le contrôle d'accès concurrentiel optimiste avec les niveaux d'isolation plus élevés, REPEATABLE READ et SERIALIZABLE. Les verrous ne sont pas utilisés pour appliquer les niveaux d'isolation. En revanche, à la fin de la transaction, une validation garantit les hypothèses de sérialisation ou de lecture renouvelable. Si les hypothèses ne sont pas respectées, la transaction est arrêtée. Pour plus d’informations, consultez [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md).

 Les sémantiques clés des transactions pour les tables mémoire optimisées sont les suivantes :

-   Contrôles de version multiples

-   Isolation d'instantané des transactions

-   Optimistic

-   Détection de conflit

 Chacune de ces sémantiques est expliquée dans les sections suivantes.

## <a name="multi-versioning-in-memory-optimized-tables"></a>Contrôles de version multiples dans les tables mémoire optimisées
 Les lignes contenues dans les tables mémoire optimisées peuvent avoir plusieurs versions. Les transactions simultanées peuvent donc accéder à des versions différentes d'une même ligne.

 Les données de tables mémoire optimisées sont fondées sur la version. Chaque ligne peut avoir plusieurs versions, valides à différents moments. Les tables sur disque conservent des versions de ligne différentes lorsque l'option READ_COMMITTED_SNAPSHOT ou ALLOW_SNAPSHOT_ISOLATION est activée (ON). Les tables mémoire optimisées conservent toujours des versions de ligne différentes, même si les options READ_COMMITTED_SNAPSHOT et ALLOW_SNAPSHOT_ISOLATION sont désactivées (OFF). Les versions de ligne des tables mémoire optimisées ne sont pas conservées dans tempdb. En revanche, elles sont conservées en ligne, dans les structures de données mémoire optimisées qui stockent les lignes en mémoire.

## <a name="snapshot-based-transaction-isolation-for-memory-optimized-tables"></a>Isolation d'instantané des transactions pour les tables mémoire optimisées
 Toutes les opérations d'une même transaction utilisent le même instantané cohérent du point de vue transactionnel des tables mémoire optimisées. Tous les niveaux d'isolation des transactions pour les tables mémoire optimisées sont basés sur un instantané. Par exemple, une transaction utilisant le niveau d'isolation SERIALIZABLE pour accéder aux tables mémoire optimisées exécute toutes les opérations dans le même instantané cohérent d'un point de vue transactionnel.

 Les transactions qui accèdent aux tables mémoire optimisées utilisent le contrôle de version de ligne pour obtenir un instantané, cohérent d'un point de vue transactionnel, des lignes contenues dans les tables. Les données lues par n'importe quelle instruction dans la transaction représenteront la version cohérente d'un point de vue transactionnel des données qui existaient au début de la transaction. Par conséquent, les modifications éventuelles apportées par d'autres transactions qui s'exécutent simultanément ne sont pas visibles par les instructions de la transaction actuelle.

## <a name="optimistic-concurrency-control-for-memory-optimized-tables"></a>Contrôle d'accès concurrentiel optimiste pour les tables mémoire optimisées
 Les conflits et les erreurs sont rares. Les transactions sur les tables mémoire optimisées partent du principe qu'il n'y a aucun conflit avec d'autres transactions simultanées et que les opérations se déroulent sans problème. Les transactions n'utilisent pas de verrous ni de verrous internes sur la table mémoire optimisée pour garantir leur isolation. Les programmes d'écriture ne bloquent pas les programmes de lecture. Les programmes d'écriture ne bloquent pas les autres programmes d'écriture. En revanche, les transactions se poursuivent dans l'hypothèse (optimiste) qu'il n'y a aucun conflit avec d'autres transactions. Le fait de ne pas utiliser de verrous ou de verrous internes et de ne pas attendre la fin de traitement des mêmes lignes par d'autres transactions améliore les performances.

 De plus, si une transaction (TxA) lit les lignes insérées ou modifiées par une autre transaction (TxB) qui est en cours de validation, le système suppose avec optimisme que l'autre transaction est validée plutôt que d'attendre la validation. Dans ce cas, la transaction TxA prend une dépendance de validation sur la transaction TxB.

## <a name="conflict-detection-validation-and-commit-dependency-checks"></a>Détection de conflit, validation et contrôles de dépendance de validation
 Si [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] détecte des conflits entre des transactions simultanées, ou des violations de niveau d'isolation, il arrête l'une des transactions en conflit. Cette transaction devra être réexécutée. (Pour plus d'informations, consultez [Guidelines for Retry Logic for Transactions on Memory-Optimized Tables](../relational-databases/in-memory-oltp/memory-optimized-tables.md).)

 Le système suppose avec optimisme qu'il n'y a aucun conflit et aucune violation d'isolation de la transaction. S'il détecte la présence de conflits pouvant provoquer des incohérences dans la base de données ou pouvant enfreindre l'isolation des transactions, il met fin à la transaction en cause.

 Lorsqu'un conflit a été détecté et la transaction arrêtée, celle-ci doit être réexécutée par le client.

 Le tableau suivant récapitule les conditions d'erreur pour les transactions qui accèdent aux tables mémoire optimisées.

### <a name="error-conditions-for-transactions-accessing-memory-optimized-tables"></a>Conditions d'erreur des transactions qui accèdent aux tables mémoire optimisées.

|Error|Scénario|
|-----------|--------------|
|Conflit d'écriture. Tentative de mettre à jour un enregistrement qui a été mis à jour depuis le début de la transaction.|Mise à jour (UPDATE) ou suppression (DELETE) d'une ligne ayant déjà été mise à jour ou supprimée par une transaction simultanée.|
|Échec de la validation de lecture renouvelable|Une ligne qui était lue par la transaction a été modifiée (mise à jour ou supprimée) depuis le début de la transaction. La validation de lecture renouvelable a généralement lieu lors de l'utilisation des niveaux d'isolation de transactions REPEATABLE READ et SERIALIZABLE.|
|Échec de la validation sérialisable|Une nouvelle ligne (fantôme) a été insérée dans l'une des plages d'analyse dans la transaction, depuis le début de la transaction. La ligne aurait été visible par la transaction si elle avait été validée dans la base de données avant le début de la transaction. La validation SERIALIZABLE a généralement lieu lors de l'utilisation de l'isolation SERIALIZABLE et de la validation des contraintes PRIMARY KEY.|
|Échec de la dépendance de validation|La transaction a pris une dépendance sur une autre transaction dont la validation a échoué, en raison de l'un des échecs indiqués dans ce tableau, d'une condition de mémoire insuffisante ou de l'échec de la validation dans le journal des transactions. Ce problème peut se produire avec des transactions de lecture/écriture et de lecture seule.|

### <a name="transaction-lifetime"></a>Durée de vie des transactions
 Les problèmes mentionnés dans le tableau précédent peuvent se produire à différents stades au cours d'une transaction. L'illustration suivante montre les phases d'une transaction qui accède à des tables mémoire optimisées.

 ![Durée de vie d'une transaction.](../../2014/database-engine/media/hekaton-transactions.gif "Durée de vie d'une transaction.")
Durée de vie d'une transaction qui accède à des tables mémoire optimisées.

#### <a name="regular-processing"></a>Traitement normal
 Durant cette phase, les instructions [!INCLUDE[tsql](../includes/tsql-md.md)] émises par l'utilisateur sont exécutées. Les lignes sont lues dans les tables, et les nouvelles versions de ligne sont écrites dans la base de données. La transaction est isolée des autres transactions simultanées. La transaction utilise l'instantané des tables mémoire optimisées tel qu'il existait au début de la transaction.

 Les écritures dans les tables durant cette phase de la transaction ne sont pas encore visibles dans les autres transactions, à une exception près : les mises à jour et les suppressions de ligne sont visibles pour les opérations de mise à jour et de suppression effectuées dans d'autres transactions, afin de détecter les conflits d'écriture.

 Si une opération de mise à jour ou de suppression détecte qu'une ligne a été mise à jour ou supprimée depuis le début logique de la transaction, l'opération échoue avec l'erreur 41302. Le message de l'erreur 41302 est « La transaction en cours a tenté de mettre à jour un enregistrement dans la table X qui a été mis à jour depuis le début de cette transaction. La transaction a été abandonnée. ».

 Cette erreur provoque l'arrêt de la transaction (même si XACT_ABORT est désactivé), ce qui signifie que la transaction sera restaurée à la fin de la session utilisateur. Les transactions vouées à l'échec ne peuvent pas être validées et prennent uniquement en charge les opérations de lecture qui n'écrivent pas dans le journal et n'accèdent pas aux tables mémoire optimisées.

#####  <a name="commit-dependencies"></a><a name="cd"></a>Dépendances de validation
 Lors du traitement normal, une transaction peut lire les lignes écrites par d'autres transactions qui sont en phase de validation, mais qui ne sont pas encore validées. Les lignes sont visibles, car l'heure de fin logique des transactions a été définie au début de la phase de validation.

 Si une transaction lit ces lignes non validées, elle prendra une dépendance de validation sur cette transaction. Cela a deux conséquences principales :

-   Une transaction ne peut pas être validée tant que les transactions dont elle dépend n'ont pas été validées. En d'autres termes, elle ne peut pas entrer dans la phase de validation tant que toutes les dépendances n'ont pas été annulées.

-   En outre, les jeux de résultats ne sont pas retournés au client tant que toutes les dépendances n'ont pas été annulées. Cela empêche le client de voir les données non validées.

 Si la validation de l'une des transactions liées échoue, il se produit une erreur de dépendance de validation. Cela signifie que la validation de la transaction échouera avec l'erreur 41301 (« Une précédente transaction dont dépend la transaction en cours s'est arrêtée et la transaction en cours ne peut plus être validée. »).

#### <a name="validation-phase"></a>Phase de validation
 Pendant la phase de validation, le système vérifie que les hypothèses nécessaires pour le niveau d'isolation de la transaction demandé étaient vraies entre le début et la fin logiques de la transaction.

 Au début de la phase de validation, une heure de fin logique est attribuée à la transaction. Les versions de ligne écrites dans la base de données deviennent accessibles à d'autres transactions à l'heure de fin logique. Pour plus d'informations, consultez [Dépendances de validation](#cd).

##### <a name="repeatable-read-validation"></a>Validation de lecture renouvelable
 Si le niveau d'isolation de la transaction est REPEATABLE READ ou SERIALIZABLE, ou que l'accès aux tables se fait avec l'isolation REPEATABLE READ ou SERIALIZABLE (pour plus d'informations, consultez la section « Isolation d'opérations individuelles » dans [Transaction Isolation Levels](../../2014/database-engine/transaction-isolation-levels.md)), le système confirme que les lectures sont renouvelables. Cela signifie que le système vérifie que les versions des lignes lues par la transaction sont des versions de ligne encore valides à l'heure de fin logique de la transaction.

 Si l'une des lignes a été mise à jour ou modifiée, la transaction échoue avec l'erreur 41305 (« La transaction en cours n'a pas été validée en raison d'un échec de validation REPEATABLE READ. »).

 Cette erreur peut également se produire si une table est supprimée après une insertion, une mise à jour ou une suppression, et avant la validation de la transaction. Cela s'applique uniquement aux opérations d'insertion, de mise à jour ou de suppression dans des procédures stockées compilées en mode natif. De telles opérations d'écriture effectuées via le langage [!INCLUDE[tsql](../includes/tsql-md.md)] interprété provoquent le blocage de l'instruction DROP TABLE, et une temporisation jusqu'à ce que la transaction soit validée.

##### <a name="serializable-validation"></a>Validation sérialisable
 La validation sérialisable est exécutée dans deux cas :

-   Le niveau d'isolation de la transaction est SERIALIZABLE ou les tables sont accessibles avec l'isolation SERIALIZABLE.

-   Les lignes sont insérées dans un index unique, tel que l'index créé pour une contrainte PRIMARY KEY. Le système vérifie qu'aucune ligne avec la même clé n'a été insérée simultanément.

 Le système vérifie qu'aucune ligne fantôme n'a été écrite dans la base de données. Les opérations de lecture effectuées par la transaction sont évaluées pour déterminer qu'aucune nouvelle ligne n'a été insérée dans les plages d'analyse de ces opérations de lecture.

 L'insertion d'une clé dans un index unique comprend une opération implicite de lecture, qui vérifie que la clé n'est pas un doublon. La validation sérialisable des index uniques garantit que ces index ne peuvent pas avoir de doublons au cas où deux transactions simultanées insèreraient la même clé.

 Si des lignes fantômes sont détectées, la transaction échoue avec l'erreur 41325 (« La transaction actuelle n'a pas été validée en raison d'un échec de validation SERIALIZABLE. »).

#### <a name="commit-processing"></a>Traitement de la validation
 Si la première phase de validation réussit et que la transaction n'a plus de dépendances, la transaction entre dans la phase de traitement de la validation. Durant cette phase, les modifications apportées aux tables durables sont écrites dans le journal, et le journal est écrit sur le disque, pour garantir la durabilité. Une fois que l'enregistrement de journal de la transaction a été écrit sur le disque, le contrôle est restitué au client.

 Toutes les dépendances de validation de la transaction sont annulées, et toutes les transactions qui attendaient la validation de cette transaction peuvent continuer à s'exécuter.

## <a name="limitations"></a>Limites

-   Les transactions de bases de données croisées ne sont pas prises en charge avec les tables mémoire optimisées. Une transaction qui accède aux tables mémoire optimisées ne peut pas accéder à plus d'une base de données, à l'exception de l'accès en lecture/écriture à tempdb et de l'accès en lecture seule à la base de données système master.

-   Les transactions distribuées ne sont pas prises en charge avec les tables mémoire optimisées. Les transactions distribuées démarrées par BEGIN DISTRIBUTED TRANSACTION ne peuvent pas accéder aux tables mémoire optimisées.

-   Les tables mémoire optimisées ne prennent pas en charge le verrouillage. Les verrous explicites via les indicateurs de verrouillage (tels que TABLOCK, XLOCK, ROWLOCK) ne sont pas pris en charge avec les tables mémoire optimisées.

## <a name="see-also"></a>Voir aussi
 [Comprendre les transactions sur les tables mémoire optimisées](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)


