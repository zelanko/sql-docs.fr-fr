---
title: Instructions pour les niveaux d’Isolation des transactions avec Tables optimisées en mémoire | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.suite: ''
ms.technology: in-memory-oltp
ms.tgt_pltfrm: ''
ms.topic: conceptual
ms.assetid: e365e9ca-c34b-44ae-840c-10e599fa614f
caps.latest.revision: 25
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 456922a60eb0d5544c2cdb7992979fea59c3da66
ms.sourcegitcommit: 79d4dc820767f7836720ce26a61097ba5a5f23f2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2018
ms.locfileid: "40394879"
---
# <a name="guidelines-for-transaction-isolation-levels-with-memory-optimized-tables"></a>Instructions pour les niveaux d'isolement des transactions sur les tables mémoire optimisées
  Dans de nombreux scénarios, vous devez spécifier le niveau d'isolation de la transaction. L'isolation des transactions pour les tables mémoire optimisées est différente de celle des tables sur disque.  
  
 Conditions requises pour spécifier le niveau d'isolation de la transaction :  
  
-   TRANSACTION ISOLATION LEVEL est une option requise pour le bloc ATOMIC contenant le contenu d'une procédure stockée compilée en mode natif.  
  
-   En raison des restrictions d'utilisation du niveau d'isolation dans les transactions entre conteneurs, l'utilisation des tables mémoire optimisées en [!INCLUDE[tsql](../includes/tsql-md.md)] interprété doit généralement être accompagnée d'un indicateur de table spécifiant le niveau d'isolation utilisé pour accéder à la table. Pour plus d’informations sur les indicateurs de niveau d’isolement et les transactions entre conteneurs, consultez [niveaux d’Isolation des transactions](../../2014/database-engine/transaction-isolation-levels.md).  
  
-   Le niveau d'isolation de la transaction souhaité doit être déclaré explicitement. Il n'est pas possible d'utiliser des indicateurs de verrouillage (tels que XLOCK) pour garantir l'isolation de certaines lignes ou tables dans la transaction.  
  
-   L'application qui accède à la base de données doit implémenter la logique de nouvelle tentative pour traiter les erreurs résultant de conflits qui condamnent la transaction, les échecs de validation et les échecs de dépendance de validation. Notez que les échecs de validation de dépendance peuvent se produire même avec les transactions en lecture seule.  
  
-   Les transactions longues doivent être évitées avec les tables mémoire optimisées. De telles transactions augmentent la probabilité des conflits et l'arrêt des transactions suivantes. Une transaction longue diffère également l'opération de garbage collection. Plus une transaction s’exécute, les versions de ligne récemment supprimée du conserve de OLTP en mémoire plus de temps, ce qui peuvent réduire les performances de recherche de nouvelles transactions.  
  
 Les tables sur disque reposent généralement sur le verrouillage et le blocage de l'isolation des transactions. Les tables mémoire optimisées reposent sur plusieurs contrôles de version et la détection de conflit pour garantir l'isolation. Pour plus d’informations, consultez la section sur la détection de conflit, Validation et contrôles de dépendance de validation dans [Transactions dans les Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Les tables sur disque permettent plusieurs contrôles de version avec les niveaux d'isolation SNAPSHOT et READ_COMMITTED_SNAPSHOT. Pour les tables mémoire optimisées, tous les niveaux d'isolation sont basés sur plusieurs contrôles de version, y compris REPEATABLE READ et SERIALIZABLE.  
  
## <a name="types-of-transactions"></a>Types de transactions  
 Chaque requête dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] s'exécute dans le contexte d'une transaction.  
  
 Il existe trois types de transactions dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
-   Transactions en mode de validation automatique. S'il n'y a pas de contexte de transaction active et les transactions implicites ne sont pas activées (ON) dans une session, chaque requête a son propre contexte de transaction. La transaction démarre lorsque l'instruction démarre l'exécution, et se termine lorsque l'instruction est terminée.  
  
-   Transactions explicites. L'utilisateur démarre la transaction via un BEGIN TRAN ou BEGIN ATOMIC explicite. La transaction est terminée après le COMMIT et ROLLBACK ou END correspondant (dans le cas d'un bloc Atomic).  
  
-   Transactions implicites. Lorsque l'option IMPLICIT_TRANSACTIONS est activée (ON), une transaction est démarrée implicitement lorsque l'utilisateur exécute une instruction et il n'y a aucun contexte de transaction active. La transaction est terminée via un COMMIT ou ROLLBACK explicite.  
  
## <a name="baseline-read-committed-isolation"></a>Isolation READ COMMITTED de base  
 READ COMMITTED est le niveau d'isolement par défaut dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].  
  
 Le niveau d'isolement READ COMMITTED garantit que les transactions ne voient aucune donnée non validée par rapport aux modifications effectuées en dehors de la transaction actuelle. En d'autres termes, la transaction lit uniquement les données qui ont été validées dans la base de données, ou modifiées par la transaction actuelle.  
  
 Tous les niveaux d'isolement pris en charge pour les tables mémoire optimisées garantissent la lecture validée. Par conséquent, si la transaction ne requiert pas de garanties plus fortes, vous pouvez utiliser n'importe quel niveau d'isolation pris en charge pour les tables mémoire optimisées. SNAPSHOT utilise moins de ressources système, par rapport à d'autres niveaux d'isolation.  
  
 La garantie fournie par le niveau d'isolation SNAPSHOT (le plus bas niveau d'isolation pris en charge pour les tables mémoire optimisées) inclut les garanties de READ COMMITTED. Chaque instruction dans la transaction lit la même version cohérente de la base de données. Non seulement les lignes sont lues par la transaction validée dans la base de données, mais toutes les opérations de lecture voient l'ensemble des modifications effectuées par le même jeu de transactions.  
  
 **Indication**: si seule la garantie d’isolation READ COMMITTED est nécessaire, utilisez l’isolation SNAPSHOT avec des procédures stockées compilées en mode natif et pour accéder aux tables mémoire optimisées via interprété [!INCLUDE[tsql](../includes/tsql-md.md)].  
  
 Pour les transactions avec validation automatique, le niveau d'isolation READ COMMITTED est mappé implicitement pour les tables mémoire optimisées. Par conséquent, si le paramètre de session TRANSACTION ISOLATION LEVEL est défini sur READ COMMITTED, il n'est pas nécessaire de spécifier le niveau d'isolation par un indicateur de table lors de l'accès aux tables mémoire optimisées.  
  
 L'exemple de transaction avec validation automatique suivant montre une jointure entre la table mémoire optimisée Customers et une table standard [Order History], dans le cadre d'un traitement ad hoc :  
  
```tsql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED;  
GO  
SELECT *   
FROM dbo.Customers AS c   
LEFT JOIN dbo.[Order History] AS oh   
    ON c.customer_id = oh.customer_id;  
```  
  
 L'exemple de transactions, explicites ou implicites, suivant utilise la même jointure, mais cette fois, dans une transaction utilisateur explicite. La table mémoire optimisée Customers est accessible avec l'isolation d'instantané, comme défini par l'indicateur de table WITH (SNAPSHOT), et la table normale [Order History] est accessible avec l'isolation READ COMMITTED :  
  
```tsql  
SET TRANSACTION ISOLATION LEVEL READ COMMITTED  
GO  
BEGIN TRAN  
SELECT * FROM dbo.Customers c with (SNAPSHOT)   
LEFT JOIN dbo.[Order History] oh   
    ON c.customer_id=oh.customer_id  
…  
COMMIT  
```  
  
### <a name="operational-differences"></a>Différences de fonctionnement  
 Outre la garantie de lecture validée, il existe deux autres points clés dont il faut tenir compte lors de l'implémentation d'applications qui utilisent des tables sur disque. Tenez compte des points suivants lors de la conversion d'une table sur disque accessible avec l'isolation READ COMMITTED vers une table mémoire optimisée accessible avec l'isolation SNAPSHOT :  
  
-   L'implémentation du niveau d'isolation READ COMMITTED pour les tables sur disque (en supposant que READ_COMMITTED_SNAPSHOT est désactivé (OFF)) utilise des verrous pour éviter les conflits entre les lecteurs et les enregistreurs. Lorsqu'un enregistreur commence à mettre à jour une ligne, il prend un verrou et ne le libère pas tant que la transaction n'est pas validée. Toutes les opérations de lecture sont bloquées et attendent la validation de la transaction d'écriture.  
  
     Certaines applications peuvent supposer que les lecteurs attendent toujours la validation des enregistreurs, notamment s'il y a une synchronisation entre les deux transactions dans la couche Application.  
  
     **Indication :** Applications ne peut pas se fier au blocage de comportement. Si une application nécessite une synchronisation entre des transactions simultanées, cette logique peut être implémentée dans la couche application ou au niveau de la base de données, via [sp_getapplock &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-getapplock-transact-sql).  
  
-   Dans les transactions qui utilisent l'isolation READ COMMITTED, chaque instruction voit la dernière version des lignes dans la base de données. Par conséquent, les instructions suivantes voient les modifications de l'état de la base de données.  
  
     Interroger une table avec une boucle WHILE jusqu'à ce qu'une nouvelle ligne soit détectée est un exemple de modèle d'application qui utilise cette hypothèse. Avec chaque itération de la boucle, la requête verra les dernières mises à jour dans la base de données.  
  
     **Indication :** si une application doit interroger une table optimisée en mémoire pour obtenir les lignes les plus récentes écrites dans la table, déplacez la boucle d’interrogation en dehors de l’étendue de la transaction.  
  
     Voici un exemple de modèle d'application qui utilise cette hypothèse. Interroger une table avec une boucle WHILE jusqu'à ce qu'une nouvelle ligne soit détectée. Dans chaque itération de la boucle, la requête accède aux dernières mises à jour dans la base de données.  
  
 L'exemple de script suivant interroge une table t1 jusqu'à ce qu'il obtienne une ligne. Une seule ligne de la table est ensuite supprimée pour un traitement ultérieur.  
  
 Notez que la logique d'interrogation doit être en dehors de l'étendue de la transaction, car elle utilise l'isolation d'instantané pour accéder à la table t1. L'utilisation de la logique d'interrogation au sein de l'étendue d'une transaction créerait une transaction longue, ce qui est une mauvaise pratique.  
  
```tsql  
-- poll table  
WHILE NOT EXISTS (SELECT 1 FROM dbo.t1)  
BEGIN   
  -- if empty, wait and poll again  
  WAITFOR DELAY '00:00:01'  
END  
  
BEGIN TRANSACTION  
  DECLARE @id int  
  SELECT TOP 1 @id=id FROM dbo.t1 WITH (SNAPSHOT)  
  DELETE FROM dbo.t1 WITH (SNAPSHOT) WHERE id=@id  
  
  -- insert processing based on @id  
COMMIT  
```  
  
## <a name="locking-table-hints"></a>Indicateurs de table de verrouillage  
 Indicateurs de verrouillage ([indicateurs de Table &#40;Transact-SQL&#41;](/sql/t-sql/queries/hints-transact-sql-table)) tels que HOLDLOCK et XLOCK peuvent être utilisés avec les tables sur disque pour avoir [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] prenne plus de verrous que nécessaire pour le niveau d’isolation spécifié.  
  
 Les tables mémoire optimisées n'utilisent pas de verrous. Des niveaux d'isolation plus élevés comme REPEATABLE READ et SERIALIZABLE peuvent être utilisés pour déclarer les garanties de votre choix.  
  
 Les indicateurs de verrouillage ne sont pas pris en charge. En revanche, déclarez les garanties requises via les niveaux d'isolation des transactions. (NOLOCK est pris en charge, car [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] n'utilise pas de verrous sur les tables mémoire optimisées. Notez que contrairement, aux tables sur disque, NOLOCK n'implique pas le comportement UNCOMMITTED READ pour les tables mémoire optimisées.)  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transactions sur les Tables optimisées en mémoire](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Logique de nouvelle tentative pour les instructions pour les Transactions sur les Tables optimisées en mémoire](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)   
 [Niveaux d’isolation de la transaction](../../2014/database-engine/transaction-isolation-levels.md)  
  
  
