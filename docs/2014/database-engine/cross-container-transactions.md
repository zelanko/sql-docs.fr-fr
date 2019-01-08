---
title: Les Transactions entre conteneurs | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: 5d84b51a-ec17-4c5c-b80e-9e994fc8ae80
author: stevestein
ms.author: sstein
manager: craigg
ms.openlocfilehash: 40420db76ee8ce5b1fcf1d085a78d7b17690105d
ms.sourcegitcommit: 2429fbcdb751211313bd655a4825ffb33354bda3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "52538594"
---
# <a name="cross-container-transactions"></a>Transactions entre conteneurs
  Les transactions entre conteneurs sont des transactions utilisateur implicites ou explicites qui incluent des appels aux procédures stockées compilées en mode natif ou des opérations sur des tables mémoire optimisées.  
  
 Dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], les appels aux procédures stockées ne démarrent pas une transaction. Les exécutions de procédures compilées en mode natif qui sont effectuées en mode de validation automatique (hors du contexte d'une transaction utilisateur) ne sont pas considérées comme des transactions entre conteneurs.  
  
 Toute requête interprétée référençant des tables mémoire optimisées est considérée comme une partie d'une transaction entre conteneurs, qu'elle soit exécutée à partir d'une transaction explicite ou implicite, ou en mode de validation automatique.  
  
##  <a name="isolation"></a> Isolation d’opérations individuelles  
 Chaque transaction [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] est caractérisée par un niveau d'isolation. Le niveau d'isolation par défaut est READ COMMITTED. Pour utiliser un niveau d’isolation différent, vous pouvez définir le niveau d’isolation à l’aide [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).  
  
 Il est souvent nécessaire d'effectuer des opérations sur les tables mémoire optimisées avec un niveau d'isolation différent des opérations sur les tables sur disque. Dans une transaction, il est possible de définir un niveau d'isolation différent pour un ensemble d'instructions ou pour une opération de lecture individuelle.  
  
### <a name="specifying-the-isolation-level-of-individual-operations"></a>Spécifier le niveau d'isolation d'opérations individuelles  
 Pour définir un niveau d'isolation différent pour un ensemble d'instructions dans une transaction, vous pouvez utiliser `SET TRANSACTION ISOLATION LEVEL`. L'exemple de transaction suivant utilise le niveau d'isolation SERIALIZABLE comme valeur par défaut. Les opérations d'insertion et de sélection sur t3, t2 et t1 sont exécutées avec l'isolation REPEATABLE READ.  
  
```tsql  
set transaction isolation level serializable  
go  
  
begin transaction  
 ......  
  set transaction isolation level repeatable read  
  
  insert t3 select * from t1 join t2 on t1.id=t2.id  
  
  set transaction isolation level serializable  
 ......  
commit  
```  
  
 Pour définir un niveau d'isolation pour certaines opérations de lecture différent de la valeur par défaut de la transaction, vous pouvez utiliser un indicateur de table (par exemple, SERIALIZABLE). Chaque sélection correspond à une opération de lecture, et chaque mise à jour et chaque suppression correspondent à une lecture, car la ligne doit toujours être lue avant de pouvoir être mise à jour ou supprimée. Les opérations d'insertion n'ont pas de niveau d'isolation, car les écritures sont toujours isolées dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Dans l'exemple suivant, le niveau d'isolation de la transaction est READ COMMITTED, mais la table t1 est accessible avec l'isolation SERIALIZABLE, et t2 avec l'isolation SNAPSHOT.  
  
```tsql  
set transaction isolation level read committed  
go  
  
begin transaction  
 ......  
  
  insert t3 select * from t1 (serializable) join t2 (snapshot) on t1.id=t2.id  
  
  ......  
commit  
```  
  
### <a name="isolation-semantics-for-individual-operations"></a>Sémantique d'isolation d'opérations individuelles  
 Une transaction sérialisable T est exécutée avec l'isolation complète. C'est comme si chaque autre transaction avait été soit validée avant le démarrage de T, soit démarrée après la validation de T. Cela devient plus complexe lorsque plusieurs opérations dans une transaction présentent des niveaux d'isolation différents.  
  
 La sémantique générale des niveaux d’isolation de transaction dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], et les conséquences sur le verrouillage, est expliqué dans [SET TRANSACTION ISOLATION LEVEL &#40;Transact-SQL&#41;](/sql/t-sql/statements/set-transaction-isolation-level-transact-sql).  
  
 Pour les transactions entre conteneurs dans lesquelles les opérations peuvent avoir différents niveaux d'isolation, vous devez comprendre la sémantique de l'isolation des opérations de lecture individuelles. Les opérations d'écriture sont toujours isolées. Les écritures effectuées dans des transactions distinctes n'ont aucun impact les unes sur les autres.  
  
 Une opération de lecture de données retourne plusieurs lignes répondant à une condition de filtre.  
  
 Les lectures sont effectuées comme partie une transaction T. niveau d’Isolation pour les opérations de lecture permettre être interprétés comme suit,  
  
 État de validation  
 L'état de validation indique si la validation de la lecture de données est garantie.  
  
 Cohérence (Transactions)  
 La cohérence transactionnelle pour un ensemble de lectures vérifie si toutes les versions de ligne lues comprennent les mises à jour du même ensemble de transactions précisément.  
  
 La stabilité garantit que le système permet à la transaction T de lire les données.  
 La stabilité détermine si les lectures des transactions sont renouvelables. c'est-à-dire si les lectures renouvelées retournent les mêmes lignes et versions de ligne.  
  
 Certaines garanties font référence à l'heure de fin logique de la transaction. En général, l'heure de fin logique est l'heure à laquelle la transaction est validée dans la base de données. Si la transaction accède à des tables mémoire optimisées, l'heure de fin logique correspond techniquement au début de la phase de validation. (Pour plus d’informations, consultez la discussion de durée de vie de transaction dans [Transactions dans les Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
 Indépendamment du niveau d'isolation, une transaction (T) voit toujours ses propres mises à jour :  
  
 READ UNCOMMITTED  
 La lecture de données ne peut être ni validée, ni cohérente, ni stable. Toutefois, cela inclut les opérations d'écriture effectuées antérieurement par T.  
  
 READ COMMITTED  
 La lecture de données est validée.  
  
 SNAPSHOT  
 Toutes les opérations de lecture effectuées par T avec l'isolation d'instantané ont la même heure de lecture logique, correspondant au début de la transaction. La validation et la cohérence de la lecture de données sont garanties à compter de l'heure logique de lecture. La répétition d'une lecture à compter de l'heure de lecture d'origine retourne toujours le même résultat.  
  
 REPEATABLE READ  
 La validation et la stabilité de la lecture de données sont garanties jusqu'à l'heure de fin logique de la transaction.  
  
 SERIALIZABLE  
 Toutes les garanties de lecture RENOUVELÉE plus empêcher les lignes fantômes et la cohérence transactionnelle sont toutes les opérations de lecture sérialisables effectuées par T. fantôme évitement signifie que l’opération d’analyse peut retourner uniquement les lignes supplémentaires écrites par T, mais aucune lignes qui ont été écrits par d’autres transactions.  
  
 Prenons l'exemple de transaction suivante :  
  
```tsql  
set transaction isolation level read committed  
go  
  
begin transaction  
  -- remove all rows from t3; the related read operation is performed under read committed   
  -- isolation, as this is the default for the transaction  
  delete from t3  
  
  -- copy the contents from t1 to t3; the read on t1 is performed under the serializable   
  -- isolation level  
  insert t3 select * from t1 (serializable)  
  
  -- compare t3 and t1; note: the result set may not be empty, as rows may have been added   
  -- by other transaction before this select, due to the read committed isolation level  
  select * from t3 except t1  
  
  -- compare t1 and t3; note: the result set is empty, as no rows have been added to t1   
  -- since its contents were copied to t1, due to the serializable isolation level  
  select * from t1 except t3  
commit  
```  
  
 Cette transaction supprime toutes les lignes de t3 avec l'isolation READ COMMITTED, copie toutes les lignes de t1 à t3 avec l'isolation SERIALIZABLE, puis compare t1 et t3. Certaines lignes [pas dans t1] peuvent avoir été ajoutées à t3, car la table a été vidée. Aucune ligne n'a été ajoutée à t1, car la copie était sérialisable.  
  
 Bien que la lecture depuis t1 à la fin de la transaction soit syntaxiquement une lecture validée, elle est en réalité sérialisable, car la même lecture a été exécutée précédemment dans la transaction avec l'isolation sérialisable : la sérialisation garantit que si la lecture est exécutée au niveau d'un point ultérieur de la transaction, les mêmes lignes sont retournées.  
  
## <a name="cross-container-transactions-and-isolation-levels"></a>Transactions entre conteneurs et niveaux d'isolation  
 Une transaction entre conteneurs peut être considérée comme ayant deux côtés : un côté sur disque (pour les opérations sur les tables sur disque) et un côté mémoire optimisé (pour les opérations sur les tables optimisées en mémoire). Ces deux côtés peuvent avoir des niveaux d'isolation différents. En fait, les opérations de lecture individuelles réalisées de chaque côté peuvent avoir des niveaux d'isolation différents.  
  
 Le côté sur disque d'une transaction T atteint un certain niveau d'isolation X si au moins une des conditions suivantes est remplie :  
  
-   Il commence à X. Autrement dit, la valeur par défaut de la session est X, soit parce que vous avez exécuté `SET TRANSACTION ISOLATION LEVEL`, ou il s’agit du [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] par défaut.  
  
-   Pendant la transaction, le niveau d'isolation est remplacé par X à l'aide de `SET TRANSACTION ISOLATION LEVEL`.  
  
-   Une opération de lecture dans une table sur disque est exécutée avec le niveau d'isolation X, à l'aide de la syntaxe `WITH (X)`.  
  
 Le côté mémoire optimisé de T atteint le niveau d'isolation Y si, pendant l'exécution de T, l'une des opérations de lecture dans une table mémoire optimisée ou l'une des procédures stockées compilées en mode natif est exécutée avec le niveau d'isolation Y.  
  
 Prenons l'exemple de la transaction suivante. Ici, t1 et t2 sont des tables sur disque, et t3 et t4 sont des tables mémoire optimisées.  
  
 Le côté sur disque de la transaction atteint le niveau d'isolation READ COMMITTED, car il commence dans ce niveau. Il atteint également le niveau REPEATABLE READ, car la première opération de lecture est exécutée avec ce niveau d'isolation. La suppression à la fin de la transaction est exécutée avec le niveau d'isolation READ COMMITTED, et n'introduit donc pas de nouveau niveau d'isolation.  
  
 Le côté mémoire optimisé de la transaction peut atteindre l'un des deux niveaux d'isolation suivants : si la condition 1 est « True », il atteint le niveau SERIALIZABLE, tandis que si elle est « False », il n'atteint que le niveau SNAPSHOT.  
  
```tsql  
set transaction isolation level read committed  
go  
  
begin transaction  
  select * from t1 (repeatableread)  
  
  if condition1 begin  
    insert t3 select * from t4 (serializable)  
  end  
  else begin  
    insert t3 select * from t4 (snapshot)  
  end  
  
  delete from t1  
commit  
```  
  
### <a name="supported-isolation-levels-for-cross-container-transactions"></a>Niveaux d'isolation pris en charge pour les transactions entre conteneurs  
 Certaines limitations s'appliquent aux niveaux d'isolation utilisés pour les opérations sur des tables mémoire optimisées dans les transactions entre conteneurs.  
  
 Les tables mémoire optimisées prennent en charge les niveaux d'isolation SNAPSHOT, REPEATABLE READ et SERIALIZABLE. Pour les transactions validées automatiquement, les tables mémoire optimisées prennent en charge le niveau d'isolation READ COMMITTED.  
  
 Les scénarios suivants sont pris en charge :  
  
-   Les transactions entre conteneurs READ UNCOMMITTED, READ COMMITTED et READ_COMMITTED_SNAPSHOT peuvent accéder aux tables mémoire optimisées avec les niveaux d'isolation SNAPSHOT, REPEATABLE READ et SERIALIZABLE. La garantie READ COMMITTED protège la transaction, car toutes les lignes lues par la transaction ont été validées dans la base de données.  
  
-   Les transactions REPEATABLE READ et SERIALIZABLE peuvent accéder aux tables mémoire optimisées avec l'isolation SNAPSHOT.  
  
## <a name="read-only-cross-container-transactions"></a>Transactions en lecture seule entre conteneurs  
 La plupart des transactions en lecture seule dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sont restaurées au moment de la validation. Étant donné qu'il n'y a aucune modification à valider sur la base de données, le système libère simplement les ressources utilisées par la transaction. Pour les transactions sur disque en lecture seule, tous les verrous pris par la transaction sont libérés à ce moment-là. Dans le cas des transactions mémoire optimisées qui sont en lecture seule et qui incluent une seule exécution de procédure stockée compilée en mode natif, aucune validation n'est effectuée.  
  
 Les transactions en lecture seule entre conteneurs qui sont exécutées en mode de validation automatique sont simplement restaurées une fois leur exécution terminée. Aucune validation n'est effectuée.  
  
 Les transactions en lecture seule, explicites ou implicites, entre conteneurs exécutent la validation à l'heure prédéfinie si elles accèdent aux tables mémoire optimisées avec l'isolation REPEATABLE READ ou SERIALIZABLE. Pour plus d’informations sur la validation de voir la section sur la détection de conflit, Validation, et contrôles de dépendance de validation dans [Transactions dans les Tables optimisées en mémoire](../relational-databases/in-memory-oltp/memory-optimized-tables.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Présentation des Transactions sur les Tables optimisées en mémoire](../../2014/database-engine/understanding-transactions-on-memory-optimized-tables.md)   
 [Instructions pour les niveaux d’Isolation des transactions avec Tables optimisées en mémoire](../../2014/database-engine/guidelines-for-transaction-isolation-levels-with-memory-optimized-tables.md)   
 [Instructions pour la logique de nouvelle tentative des transactions sur des tables à mémoire optimisée](../../2014/database-engine/guidelines-for-retry-logic-for-transactions-on-memory-optimized-tables.md)  
  
  
