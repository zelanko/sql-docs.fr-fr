---
title: Création de procédures stockées compilées en mode natif | Microsoft Docs
ms.custom: ''
ms.date: 03/06/2017
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: in-memory-oltp
ms.topic: conceptual
ms.assetid: e6b34010-cf62-4f65-bbdf-117f291cde7b
author: CarlRabeler
ms.author: carlrab
manager: craigg
ms.openlocfilehash: 72c72dc551aa31dc22def397fb38fe09793478ef
ms.sourcegitcommit: 3da2edf82763852cff6772a1a282ace3034b4936
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2018
ms.locfileid: "48084509"
---
# <a name="creating-natively-compiled-stored-procedures"></a>Création de procédures stockées compilées en mode natif
  Les procédures stockées compilées en mode natif n'implémentent pas la surface d'exposition totale de programmabilité et de requête [!INCLUDE[tsql](../../includes/tsql-md.md)] . Certaines constructions [!INCLUDE[tsql](../../includes/tsql-md.md)] ne peuvent pas être utilisées dans des procédures stockées compilées en mode natif. Pour plus d’informations, consultez [constructions prises en charge dans Natively Compiled Stored Procedures](..\in-memory-oltp\supported-features-for-natively-compiled-t-sql-modules.md).  
  
 À l'inverse, plusieurs fonctionnalités [!INCLUDE[tsql](../../includes/tsql-md.md)] ne sont prises en charge que pour les procédures stockées compilées en mode natif :  
  
-   Blocs Atomic. Pour plus d’informations, consultez [Atomic Blocks](atomic-blocks-in-native-procedures.md).  
  
-   Contraintes `NOT NULL` sur les paramètres et les variables de procédures stockées compilées en mode natif. Vous ne pouvez pas affecter de valeurs `NULL` aux paramètres ou aux variables déclarés en tant que `NOT NULL`. Pour plus d’informations, consultez [DECLARE @local_variable &#40;Transact-SQL&#41;](/sql/t-sql/language-elements/declare-local-variable-transact-sql).  
  
-   Liaison de schéma des procédures stockées compilées en mode natif.  
  
 Les procédures stockées compilées en mode natif sont créées à l’aide de [CREATE PROCEDURE &#40;Transact-SQL&#41;](/sql/t-sql/statements/create-procedure-transact-sql). L'exemple suivant illustre une table optimisée en mémoire et une procédure stockée compilée en mode natif utilisée pour insérer des lignes dans la table.  
  
```tsql  
create table dbo.Ord  
(OrdNo integer not null primary key nonclustered,   
 OrdDate datetime not null,   
 CustCode nvarchar(5) not null)   
 with (memory_optimized=on)  
go  
  
create procedure dbo.OrderInsert(@OrdNo integer, @CustCode nvarchar(5))  
with native_compilation, schemabinding, execute as owner  
as   
begin atomic with  
(transaction isolation level = snapshot,  
language = N'English')  
  
  declare @OrdDate datetime = getdate();  
  insert into dbo.Ord (OrdNo, CustCode, OrdDate) values (@OrdNo, @CustCode, @OrdDate);  
end  
go  
```  
  
 Dans l’exemple de code, `NATIVE_COMPILATION` indique que ce [!INCLUDE[tsql](../../includes/tsql-md.md)] procédure stockée est une procédure stockée compilée en mode natif. Les options suivantes sont requises :  
  
|Option|Description|  
|------------|-----------------|  
|`SCHEMABINDING`|Les procédures stockées compilées en mode natif doivent être liés au schéma des objets référencés. Cela signifie que la table référencée par la procédure ne peut pas être supprimée. Tables référencées dans la procédure doivent inclure leur nom de schéma et les caractères génériques (\*) ne sont pas autorisés dans les requêtes. `SCHEMABINDING` est uniquement pris en charge pour les procédures stockées compilées en mode natif dans cette version de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].|  
|`EXECUTE AS`|Les procédures stockées compilées en mode natif ne prennent pas en charge `EXECUTE AS CALLER`, qui est le contexte d'exécution par défaut. Par conséquent, vous devez spécifier le contexte d'exécution. Les options `EXECUTE AS OWNER`, `EXECUTE AS` *utilisateur*, et `EXECUTE AS SELF` sont pris en charge.|  
|`BEGIN ATOMIC`|Le corps d'une procédure stockée compilée en mode natif doit être un bloc Atomic. Les blocs Atomic garantissent l'exécution atomique de la procédure stockée. Si la procédure est appelée en dehors du contexte d'une transaction active, elle démarre une nouvelle transaction, qui valide la transaction à la fin du bloc Atomic. Deux options sont obligatoires pour les blocs Atomic dans les procédures stockées compilées en mode natif :<br /><br /> `TRANSACTION ISOLATION LEVEL` . Consultez [Transaction Isolation Levels](../../database-engine/transaction-isolation-levels.md) pour les niveaux d’isolation pris en charge.<br /><br /> `LANGUAGE` . Le langage de la procédure stockée doit être défini sur l'un des langages ou des alias de langage disponibles.|  
  
 En ce qui concerne `EXECUTE AS` et les connexions Windows, une erreur peut se produire en raison de l'emprunt d'identité effectué via `EXECUTE AS`. Si un compte d'utilisateur utilise l'authentification Windows, il doit y avoir une confiance totale entre le compte de service utilisé pour l'instance de [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] et le domaine de la connexion Windows. S'il n'y a pas de confiance totale, le message d'erreur suivant est retourné lorsque vous créez une procédure stockée compilée en mode natif : Message 15404, Impossible d'obtenir des informations sur le groupe Windows NT/utilisateur « nom d'utilisateur », code d'erreur 0x5.  
  
 Pour résoudre cette erreur, utilisez une des opérations suivantes :  
  
-   Utilisez un compte du même domaine que l'utilisateur Windows pour le service [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
-   Si [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)] est à l’aide d’un compte d’ordinateur comme Service réseau ou système Local, l’ordinateur doit être approuvé par le domaine contenant l’utilisateur Windows.  
  
-   Utilisez l'authentification [!INCLUDE[ssNoVersion](../../../includes/ssnoversion-md.md)].  
  
 L'erreur 15517 s'affiche également lorsque vous créez une procédure stockée compilée en mode natif. Pour plus d’informations, consultez [MSSQLSERVER_15517](../errors-events/mssqlserver-15517-database-engine-error.md).  
  
## <a name="updating-a-natively-compiled-stored-procedure"></a>Mise à jour d'une procédure stockée compilée en mode natif  
 L'exécution d'opérations de modification (ALTER) sur les procédures stockées compilées en mode natif n'est pas prise en charge. Une méthode pour modifier une procédure stockée compilée en mode natif consiste à supprimer et recréer la procédure stockée :  
  
1.  Générez un script d'autorisations sur la procédure stockée.  
  
2.  Éventuellement, générez un script pour la procédure stockée et enregistrez-le comme sauvegarde.  
  
3.  Supprimez la procédure stockée.  
  
4.  Créez la procédure stockée modifiée.  
  
5.  Réappliquez les autorisations du script à la procédure stockée.  
  
 L’inconvénient de cette procédure est que l’application sera hors connexion à partir du début de l’étape 3 à l’issue de l’étape 5. Cette opération peut prendre quelques secondes et le client qui utilise l'application peut recevoir des messages d'erreur.  
  
 Une autre méthode pour modifier (efficacement) une procédure stockée compilée en mode natif consiste à créer, dans un premier temps, une nouvelle version de la procédure stockée. La procédure stockée compilée en mode natif possède un numéro de version associé. Nous allons nommer l'ancienne version SP_Vold et la nouvelle SP_Vnew.  
  
1.  Générez un script d'autorisations sur SP_Vold  
  
2.  Créez SP_Vnew.  
  
3.  Appliquez les autorisations de SP_Vold à SP_new.  
  
4.  Mettez à jour les références à SP_Vold de façon à ce qu'elles pointent vers SP_Vnew. Cette opération peut être effectuée de différentes manières, par exemple :  
  
     Utilisez une procédure stockée (sur disque) de wrapper, et modifiez-la de façon à ce qu'elle pointe vers SP_Vnew. L'inconvénient de cette méthode est l'impact de l'indirection sur les performances.  
  
    ```tsql  
    ALTER PROCEDURE dbo.SP p1,...,pn  
    AS  
      EXEC dbo.SP_Vnew p1,...,pn  
    GO  
    ```  
  
5.  Supprimez éventuellement SP_Vold.  
  
 L'avantage de cette méthode est que l'application n'est pas mise hors connexion. En revanche, cette méthode nécessite davantage de travail pour gérer les références et veiller à ce qu'elles pointent toujours vers la version la plus récente de la procédure stockée.  
  
## <a name="see-also"></a>Voir aussi  
 [Procédures stockées compilées en mode natif](natively-compiled-stored-procedures.md)  
  
  
