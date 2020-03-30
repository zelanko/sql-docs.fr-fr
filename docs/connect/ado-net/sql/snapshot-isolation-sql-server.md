---
title: Isolation d’instantanés dans SQL Server
description: Décrit la prise en charge de l’isolation d’instantané, un mécanisme de contrôle de version de ligne conçu pour réduire les blocages dans les applications transactionnelles.
ms.date: 08/15/2019
dev_langs:
- csharp
ms.assetid: 43ae5dd3-50f5-43a8-8d01-e37a61664176
ms.prod: sql
ms.prod_service: connectivity
ms.technology: connectivity
ms.topic: conceptual
author: rothja
ms.author: jroth
ms.reviewer: v-kaywon
ms.openlocfilehash: 35b19b89a0539d9cc07bca0b1f09efda71cd5624
ms.sourcegitcommit: ff82f3260ff79ed860a7a58f54ff7f0594851e6b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2020
ms.locfileid: "78896612"
---
# <a name="snapshot-isolation-in-sql-server"></a>Isolation d’instantanés dans SQL Server

[!INCLUDE[Driver_ADONET_Download](../../../includes/driver_adonet_download.md)]

L’isolation d’instantané améliore l’accès concurrentiel pour les applications OLTP.  
  
## <a name="understanding-snapshot-isolation-and-row-versioning"></a>Fonctionnement de l’isolation d’instantané et du contrôle de version de ligne  
Une fois l’isolation d’instantané activée, les versions de ligne mise à jour pour chaque transaction sont conservées dans **tempdb**. Un numéro de séquence de transaction unique identifie chaque transaction, et ces numéros uniques sont enregistrés pour chaque version de ligne. La transaction fonctionne avec les versions de ligne les plus récentes ayant un numéro de séquence antérieur au numéro de séquence de la transaction. Les versions de ligne plus récentes créées après le début de la transaction sont ignorées par la transaction.  
  
Le terme « instantané » reflète le fait que toutes les requêtes de la transaction voient la même version, ou instantané, de la base de données, en fonction de l’état de la base de données au moment où la transaction commence. Aucun verrou n’est acquis sur les lignes de données ou les pages de données sous-jacentes dans une transaction d’instantané, ce qui permet à d’autres transactions de s’exécuter sans être bloquées par une transaction antérieure inachevée. Les transactions qui modifient des données ne bloquent pas les transactions qui lisent des données, et les transactions qui lisent des données ne bloquent pas les transactions qui écrivent des données, comme elles le feraient normalement avec le niveau d’isolation READ COMMITTED par défaut dans SQL Server. Ce comportement non bloquant réduit également sensiblement la probabilité de blocages pour les transactions complexes.  
  
L’isolation d’instantané utilise un modèle d’accès concurrentiel optimiste. Si une transaction d’instantané tente de valider des modifications apportées à des données qui ont été modifiées après le début de la transaction, la transaction est annulée et une erreur est générée. Vous pouvez éviter cela en utilisant des indicateurs UPDLOCK pour les instructions SELECT qui accèdent aux données à modifier. Pour plus d’informations, consultez « Indicateurs de verrouillage » dans la Documentation en ligne de SQL Server.  
  
L’isolation d’instantané doit être activée en définissant l’option ALLOW_SNAPSHOT_ISOLATION sur la base de données avant qu’elle soit utilisée dans des transactions. Cela active le mécanisme de stockage de versions de ligne dans la base de données temporaire (**tempdb**). Vous devez activer l’isolation d’instantané dans chaque base de données qui l’utilise avec l’instruction Transact-SQL ALTER DATABASE. À cet égard, l’isolation d’instantané diffère des niveaux d’isolation traditionnels READ COMMITTED, REPEATABLE READ, SERIALIZABLE et READ UNCOMMITTED, qui ne nécessitent aucune configuration. Les instructions suivantes activent l’isolation d’instantané et remplacent le comportement READ COMMITTED par défaut par SNAPSHOT :  
  
```sql  
ALTER DATABASE MyDatabase  
SET ALLOW_SNAPSHOT_ISOLATION ON  
  
ALTER DATABASE MyDatabase  
SET READ_COMMITTED_SNAPSHOT ON  
```  
  
La définition de l’option READ_COMMITTED_SNAPSHOT ON permet d’accéder aux lignes avec version sous le niveau d’isolation READ COMMITTED par défaut. Si l’option READ_COMMITTED_SNAPSHOT est désactivée (OFF), vous devez définir explicitement le niveau d’isolation d’instantané pour chaque session afin d’accéder aux lignes avec version.  
  
## <a name="managing-concurrency-with-isolation-levels"></a>Gestion de l’accès concurrentiel avec des niveaux d’isolation  
Le niveau d’isolation sous lequel une instruction Transact-SQL s’exécute détermine son comportement de verrouillage et de contrôle de version de ligne. Un niveau d’isolation a une portée à l’échelle de la connexion et, une fois défini pour une connexion avec l’instruction SET TRANSACTION ISOLATION LEVEL, il reste effectif jusqu’à ce que la connexion soit fermée ou qu’un autre niveau d’isolation soit défini. Lorsqu’une connexion est fermée et retournée au pool, le niveau d’isolation de la dernière instruction SET TRANSACTION ISOLATION LEVEL est conservé. Les connexions suivantes réutilisant une connexion regroupée utilisent le niveau d’isolation en vigueur au moment où la connexion est regroupée.  
  
Les requêtes individuelles émises au sein d’une connexion peuvent contenir des indicateurs de verrou qui modifient l’isolation pour une seule instruction ou transaction, mais n’affectent pas le niveau d’isolation de la connexion. Les niveaux d’isolation ou les indicateurs de verrou définis dans les procédures stockées ou les fonctions ne modifient pas le niveau d’isolation de la connexion qui les appelle et ne sont effectifs que pendant la durée de la procédure stockée ou de l’appel de fonction.  
  
Quatre niveaux d’isolation définis dans la norme SQL-92 étaient pris en charge dans les premières versions de SQL Server :  
  
- READ UNCOMMITTED est le niveau d’isolation le moins restrictif, car il ignore les verrous placés par d’autres transactions. Les transactions qui s’exécutent sous READ UNCOMMITTED peuvent lire des valeurs de données modifiées qui n’ont pas encore été validées par d’autres transactions ; celles-ci sont appelées lectures « erronées ».  
  
- READ COMMITTED est le niveau d’isolation par défaut pour SQL Server. Il empêche les lectures erronées en spécifiant que les instructions ne peuvent pas lire des valeurs de données modifiées et non encore validées par d'autres transactions. D’autres transactions peuvent toujours modifier, insérer ou supprimer des données entre les exécutions d’instructions individuelles dans la transaction en cours, ce qui aboutit à des lectures non renouvelables ou des données « fantômes ».  
  
- La lecture renouvelable est un niveau d’isolation plus restrictif que READ COMMITTED. Il englobe READ COMMITTED et spécifie qu’aucune autre transaction ne peut modifier ou supprimer des données qui ont été lues par la transaction actuelle jusqu’à ce que la transaction en cours soit validée. La concurrence est inférieure à celle de READ COMMITTED, car les verrous partagés sur les données lues sont conservés pendant la durée de la transaction au lieu d’être libérés à la fin de chaque instruction.  
  
- SERIALIZABLE est le niveau d’isolation le plus restrictif, car il verrouille des groupes de clés entiers et laisse les verrous en place jusqu’à la fin de la transaction. Il englobe la lecture renouvelable et ajoute la restriction selon laquelle les autres transactions ne peuvent pas insérer de nouvelles lignes dans les plages qui ont été lues par la transaction jusqu’à ce que la transaction soit terminée.  
  
Pour plus d’informations, consultez le [Guide du verrouillage des transactions et de la gestion de versions de ligne](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md).  
  
### <a name="snapshot-isolation-level-extensions"></a>Extensions de niveau d’isolation d’instantané  
SQL Server a introduit des extensions des niveaux d’isolation de SQL-92 avec le niveau d’isolation SNAPSHOT et l’implémentation supplémentaire de READ COMMITTED. Le niveau d’isolation READ_COMMITTED_SNAPSHOT peut remplacer de façon transparente READ COMMITTED pour toutes les transactions.  
  
- L’isolation d’instantané spécifie que les données lues dans une transaction ne refléteront jamais les modifications apportées par d’autres transactions simultanées. La transaction utilise les versions de ligne de données qui existent au début de la transaction. Aucun verrou n’est placé sur les données lors de leur lecture, de sorte que les transactions d’instantané n’empêchent pas d’autres transactions d’écrire des données. De même, les transactions qui écrivent des données n’empêchent pas des transactions d’instantanés de lire des données. Vous devez activer l’isolation d’instantané en définissant l’option ALLOW_SNAPSHOT_ISOLATION sur la base de données afin de l’utiliser.  
  
- L’option de base de données READ_COMMITTED_SNAPSHOT détermine le comportement du niveau d’isolation READ COMMITTED par défaut lorsque l’isolation d’instantané est activée dans une base de données. Si vous ne spécifiez pas explicitement READ_COMMITTED_SNAPSHOT ON, READ COMMITTED est appliqué à toutes les transactions implicites. Cela produit le même comportement que le paramètre READ_COMMITTED_SNAPSHOT OFF (valeur par défaut). Lorsque READ_COMMITTED_SNAPSHOT OFF s’applique, le moteur de base de données utilise des verrous partagés pour appliquer le niveau d’isolation par défaut. Si vous affectez la valeur ON à l’option de base de données READ_COMMITTED_SNAPSHOT, le moteur de base de données utilise le contrôle de version de ligne et l’isolation d’instantané comme valeur par défaut, au lieu d’utiliser des verrous pour protéger les données.  
  
## <a name="how-snapshot-isolation-and-row-versioning-work"></a>Fonctionnement de l’isolation d’instantané et du contrôle de version de ligne  
Quand le niveau d’isolation SNAPSHOT est activé, chaque fois qu’une ligne est mise à jour, le moteur de base de données SQL Server stocke une copie de la ligne originale dans **tempdb** et ajoute un numéro de séquence de transaction à la ligne. Voici la séquence des événements :  
  
1. Une nouvelle transaction est lancée et un numéro de séquence de transaction lui est affecté.  
  
2. Le moteur de base de données lit une ligne de la transaction et extrait la version de ligne de **tempdb** dont le numéro de séquence est le plus proche et inférieur au numéro de séquence de la transaction.  
  
3. Le moteur de base de données vérifie si le numéro de séquence de la transaction ne figure pas dans la liste des numéros de séquence de transaction des transactions non validées actives au démarrage de la transaction d’instantané.  
  
4. La transaction lit dans **tempdb** la version de la ligne telle qu’elle était au début de la transaction. Les nouvelles lignes insérées après le début de la transaction ne sont pas visibles, car leurs valeurs de numéro de séquence sont supérieures au numéro de la transaction.  
  
5. La transaction en cours voit les lignes qui ont été supprimées après le début de la transaction car il y aura une version de ligne dans **tempdb** dont la valeur de numéro de séquence est inférieure.  
  
L’effet net de l’isolation d’instantané est que la transaction voit toutes les données telles qu’elles existaient au début de la transaction, sans respecter ni placer de verrous sur les tables sous-jacentes. Cela peut entraîner des améliorations des performances dans les situations où il existe une contention.  
  
Une transaction d’instantané utilise toujours le contrôle d’accès concurrentiel optimiste, en retenant tous les verrous qui empêchent les autres transactions de mettre à jour des lignes. Si une transaction d’instantané tente de valider une mise à jour sur une ligne qui a été modifiée après le début de la transaction, la transaction est restaurée et une erreur est générée.  
  
## <a name="working-with-snapshot-isolation-in-adonet"></a>Utilisation de l’isolation d’instantané dans ADO.NET  
L’isolation d’instantané est prise en charge dans ADO.NET avec la classe <xref:Microsoft.Data.SqlClient.SqlTransaction>. Si une base de données a été activée pour l’isolation d’instantané mais n’est pas configurée pour READ_COMMITTED_SNAPSHOT ON, vous devez lancer un <xref:Microsoft.Data.SqlClient.SqlTransaction> en utilisant la valeur d’énumération **IsolationLevel.Snapshot** lors de l’appel de la méthode <xref:Microsoft.Data.SqlClient.SqlConnection.BeginTransaction%2A>. Ce fragment de code suppose que la connexion est un objet <xref:Microsoft.Data.SqlClient.SqlConnection> ouvert.  
  
```csharp  
SqlTransaction sqlTran =   
  connection.BeginTransaction(IsolationLevel.Snapshot);  
```  
  
### <a name="example"></a>Exemple  
L’exemple suivant montre comment les différents niveaux d’isolation se comportent en tentant d’accéder aux données verrouillées et n’est pas destiné à être utilisé dans du code de production.  
  
Le code se connecte à l’exemple de base de données **AdventureWorks** dans SQL Server, crée une table nommée **TestSnapshot** et insère une ligne de données. Le code utilise l’instruction Transact-SQL ALTER DATABASE pour activer l’isolation d’instantané pour la base de données, mais il ne définit pas l’option READ_COMMITTED_SNAPSHOT, ce qui laisse le comportement de niveau d’isolation READ COMMITTED par défaut en vigueur. Le code effectue ensuite les actions suivantes :  
  
1. Il commence, mais ne termine pas, sqlTransaction1, qui utilise le niveau d’isolation SERIALIZABLE pour démarrer une transaction de mise à jour. Cela a pour effet de verrouiller la table.  
  
2. Il ouvre une seconde connexion et lance une seconde transaction en utilisant le niveau d’isolation SNAPSHOT pour lire les données dans la table **TestSnapshot**. Étant donné que l’isolation d’instantané est activée, cette transaction peut lire les données qui existaient avant le démarrage de sqlTransaction1.  
  
3. Il ouvre une troisième connexion et initie une transaction en utilisant le niveau d’isolation READ COMMITTED pour tenter de lire les données de la table. Dans ce cas, le code ne peut pas lire les données car il ne peut pas lire au-delà des verrous appliqués à la table dans la première transaction et le délai de temporisation expire. Le même résultat est obtenu si les niveaux d’isolation REPEATABLE READ et SERIALIZABLE ont été utilisés, car ces niveaux ne peuvent pas non plus lire au-delà des verrous appliqués à la première transaction.  
  
4. Il ouvre une quatrième connexion et initie une transaction en utilisant le niveau d’isolation READ UNCOMMITTED, qui effectue une lecture erronée de la valeur non validée dans sqlTransaction1. Cette valeur peut ne jamais exister dans la base de données si la première transaction n’est pas validée.  
  
5. Elle annule la première transaction et nettoie en supprimant la table **TestSnapshot** et en désactivant l’isolation d’instantané pour la base de données **AdventureWorks**.  
  
> [!NOTE]
>  Les exemples suivants utilisent la même chaîne de connexion avec le regroupement de connexions désactivé. Si une connexion est regroupée, la réinitialisation de son niveau d’isolation ne rétablit pas le niveau d’isolation sur le serveur. Par conséquent, les connexions suivantes qui utilisent la même connexion interne regroupée démarrent avec leurs niveaux d’isolation définis sur ceux de la connexion regroupée. Une alternative à la désactivation du regroupement de connexions consiste à définir le niveau d’isolation de manière explicite pour chaque connexion.  
  
[!code-csharp[DataWorks Isolation_Snapshot.Demo#1](~/../sqlclient/doc/samples/Isolation_Snapshot.cs#1)]
  
### <a name="example"></a>Exemple  
L’exemple suivant illustre le comportement de l’isolation d’instantané quand des données sont modifiées. Le code effectue les actions suivantes :  
  
1. Il établit une connexion avec l’exemple de base de données **AdventureWorks** et active l’isolation SNAPSHOT.  
  
2. Il crée une table nommée **TestSnapshotUpdate** et insère trois lignes d’exemples de données.  
  
3. Commence, mais ne se termine pas, car sqlTransaction1 utilise l’isolation d’instantané. Trois lignes de données sont sélectionnées dans la transaction.  
  
4. Il crée une seconde **SqlConnection** à **AdventureWorks** et une seconde transaction utilisant le niveau d’isolation READ COMMITTED, qui met à jour une valeur dans l’une des lignes sélectionnées dans sqlTransaction1.  
  
5. Valide sqlTransaction2.  
  
6. Retourne à sqlTransaction1 et tente de mettre à jour la même ligne que celle que sqlTransaction1 a déjà validée. L’erreur 3960 est déclenchée et sqlTransaction1 est restaurée automatiquement. **SqlException.Number** et **SqlException.Message** s’affichent dans la fenêtre de console.  
  
7. Il exécute un code de nettoyage pour désactiver l’isolation d’instantané dans **AdventureWorks** et supprimer la table **TestSnapshotUpdate**.  
  
    [!code-csharp[DataWorks Isolation_Snapshot1#1](~/../sqlclient/doc/samples/Isolation_Snapshot1.cs#1)]
  
### <a name="using-lock-hints-with-snapshot-isolation"></a>Utilisation d’indicateurs de verrou avec l’isolation d’instantané  
Dans l’exemple précédent, la première transaction sélectionne des données et une deuxième transaction met à jour les données avant que la première transaction puisse se terminer, provoquant un conflit de mise à jour lorsque la première transaction tente de mettre à jour la même ligne. Vous pouvez réduire le risque de conflits de mise à jour dans les transactions d’instantanés de longue durée en fournissant des indicateurs de verrou au début de la transaction. L’instruction SELECT suivante utilise l’indicateur UPDLOCK pour verrouiller les lignes sélectionnées :  
  
```sql  
SELECT * FROM TestSnapshotUpdate WITH (UPDLOCK)   
  WHERE PriKey BETWEEN 1 AND 3  
```  
  
L’utilisation de l’indicateur de verrou UPDLOCK bloque toutes les lignes tentant de mettre à jour les lignes avant la fin de la première transaction. Cela garantit que les lignes sélectionnées n’ont aucun conflit lorsqu’elles sont mises à jour ultérieurement dans la transaction. Consultez « Indicateurs de verrouillage » dans la Documentation en ligne de SQL Server.  
  
Si votre application présente de nombreux conflits, l’isolation d’instantané n’est peut-être pas le meilleur choix. Les indicateurs doivent être utilisés uniquement lorsque cela est vraiment nécessaire. Votre application ne doit pas être conçue de manière à ce qu’elle s’appuie constamment sur des indicateurs de verrou pour son fonctionnement.  
  
## <a name="next-steps"></a>Étapes suivantes
- [SQL Server et ADO.NET](index.md)
- [Guide du verrouillage des transactions et du contrôle de version de ligne](../../../relational-databases/sql-server-transaction-locking-and-row-versioning-guide.md)
