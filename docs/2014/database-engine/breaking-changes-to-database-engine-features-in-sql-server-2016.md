---
title: Modifications importantes apportées aux fonctionnalités de Moteur de base de données dans SQL Server 2014 | Microsoft Docs
ms.custom: ''
ms.date: 01/19/2019
ms.prod: sql-server-2014
ms.reviewer: ''
ms.technology: release-landing
ms.topic: conceptual
helpviewer_keywords:
- Database Engine [SQL Server], what's new
- breaking changes [SQL Server]
ms.assetid: 47edefbd-a09b-4087-937a-453cd5c6e061
author: MikeRayMSFT
ms.author: mikeray
manager: craigg
ms.openlocfilehash: d7b5bf6ff2324c8e63b030d03e36794faf0ec9d4
ms.sourcegitcommit: 6fd8c1914de4c7ac24900fe388ecc7883c740077
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/26/2020
ms.locfileid: "67419036"
---
# <a name="breaking-changes-to-database-engine-features-in-sql-server-2014"></a>Changements essentiels dans les fonctionnalités du moteur de base de données de SQL Server 2014
  Cette rubrique décrit les [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] [!INCLUDE[ssDE](../includes/ssde-md.md)] modifications importantes apportées à et [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]aux versions antérieures de. Ces modifications peuvent interrompre les applications, scripts ou fonctionnalités fondés sur les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Il se peut que vous rencontriez ces problèmes lors d'une mise à niveau. Pour plus d'informations, consultez [Use Upgrade Advisor to Prepare for Upgrades](../sql-server/install/use-upgrade-advisor-to-prepare-for-upgrades.md).  
  
##  <a name="breaking-changes-in-sssql14"></a><a name="SQL14"></a> Modifications avec rupture dans [!INCLUDE[ssSQL14](../includes/sssql14-md.md)]  
 Aucun nouveau problème.  
  
##  <a name="breaking-changes-in-sssql11"></a><a name="Denali"></a>Modifications avec rupture dans[!INCLUDE[ssSQL11](../includes/sssql11-md.md)]  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Sélection dans des colonnes ou des tables nommées NEXT|Les séquences utilisent la fonction ANSI standard NEXT VALUE FOR. Si une table ou une colonne est nommée NEXT et que la table ou la colonne est un alias en tant que valeur, et si la norme ANSI est omise, l’instruction résultante peut provoquer une erreur. Pour contourner ce problème, incluez le mot clé ANSI standard AS. Par exemple, `SELECT NEXT VALUE FROM Table` doit être réécrit comme `SELECT NEXT AS VALUE FROM Table` et `SELECT Col1 FROM NEXT VALUE` doit être réécrit comme `SELECT Col1 FROM NEXT AS VALUE`.|  
|PIVOT (opérateur)|L'opérateur PIVOT n'est pas autorisé dans une requête d'expression de table commune récursive lorsque le niveau de compatibilité de la base de données est défini à 110. Réécrivez la requête, ou définissez un niveau de compatibilité inférieur ou égal à 100. L'utilisation de l'opérateur PIVOT dans une requête d'expression de table commune récursive génère des résultats incorrects lorsqu'il y a plusieurs lignes par regroupement.|  
|sp_setapprole et sp_unsetapprole|Le paramètre `OUTPUT` de cookie pour `sp_setapprole` est actuellement documenté comme `varbinary(8000)`, ce qui correspond à la longueur maximale correcte. Toutefois, l'implémentation actuelle retourne `varbinary(50)`. Les applications doivent continuer à réserver `varbinary(8000)` afin de continuer à fonctionner correctement si la taille de retour des cookies augmente dans une version ultérieure. Pour plus d’informations, consultez [sp_setapprole &#40;Transact-SQL&#41;](/sql/relational-databases/system-stored-procedures/sp-setapprole-transact-sql).|  
|EXECUTE AS|Le paramètre OUTPUT de cookie pour EXECUTE AS est actuellement documenté comme `varbinary(8000)`, ce qui correspond à la longueur maximale correcte. Toutefois, l'implémentation actuelle retourne `varbinary(100)`. Les applications doivent continuer à réserver `varbinary(8000)` afin de continuer à fonctionner correctement si la taille de retour des cookies augmente dans une version ultérieure. Pour plus d’informations, consultez [EXECUTE AS &#40;Transact-SQL&#41;](/sql/t-sql/statements/execute-as-transact-sql).|  
|sys.fn_get_audit_file, fonction|Deux colonnes supplémentaires (**user_defined_event_id** et **user_defined_information**) ont été ajoutées pour prendre en charge les événements d’audit définis par l’utilisateur. Les applications qui ne sélectionnent pas de colonnes par nom peuvent retourner plus de colonnes que prévu. Sélectionnez des colonnes par nom, ou modifiez l'application pour accepter ces colonnes supplémentaires.|  
|WITHIN (mot clé réservé)|WITHIN est maintenant un mot clé réservé. Les références aux objets ou aux colonnes nommés « within » échouent. Renommez l'objet ou la colonne ou délimitez le nom par des crochets ou des guillemets.  Par exemple, `SELECT * FROM [within]`.|  
|Opérations CAST et CONVERT sur des colonnes calculées de type `time` ou `datetime2`|Dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le style par défaut pour les opérations CAST et CONVERT sur les types de données `time` et `datetime2` est 121, sauf si l'un des types est utilisé dans une expression de colonne calculée. Pour les colonnes calculées, le style par défaut est 0. Ce comportement influe sur les colonnes calculées lorsqu'elles sont créées, utilisées dans des requêtes impliquant le paramétrage automatique, ou utilisées dans des définitions de contraintes.<br /><br /> Lorsque le niveau de compatibilité est 110, le style par défaut pour les opérations CAST et CONVERT sur les types de données `time` et `datetime2` est toujours 121. Si votre requête repose sur l'ancien comportement, utilisez un niveau de compatibilité inférieur à 110, ou spécifiez explicitement le style 0 dans la requête affectée.<br /><br /> La mise à niveau de la base de données vers le niveau de compatibilité 110 ne modifie pas les données utilisateur stockées sur le disque. Vous devez corriger manuellement ces données comme il convient. Par exemple, si vous avez utilisé SELECT INTO pour créer une table à partir d'une source qui contenait une expression de colonne calculée décrite ci-dessus, les données (utilisant le style 0) sont stockées à la place de la définition de colonne calculée. Vous devez mettre à jour manuellement ces données pour qu'elles correspondent au style 121.|  
|ALTER TABLE|L'instruction ALTER TABLE permet uniquement les noms de tables (schema.object) en deux parties. La spécification d’un nom de table à l’aide des formats suivants échoue désormais au moment de la compilation avec l’erreur 117 :<br /><br /> server.database.schema.table<br /><br /> .database.schema.table<br /><br /> ..schema.table<br /><br /> Dans les versions antérieures, la spécification du format server.database.schema.table retournait l'erreur 4902. La spécification du format .database.schema.table ou .schema.table aboutissait. Pour résoudre le problème, supprimez l'utilisation d'un préfixe en quatre parties.|  
|Exploration des métadonnées|L'interrogation d'une vue à l'aide de FOR BROWSE ou SET NO_BROWSETABLE ON retourne maintenant les métadonnées de la vue, et non pas les métadonnées de l'objet sous-jacent. Ce comportement correspond désormais à d'autres méthodes d'exploration de métadonnées.|  
|SOUNDEX|Lorsque le niveau de compatibilité de la base de données est défini à 110, la fonction SOUNDEX implémente de nouvelles règles qui peuvent générer des valeurs calculées par la fonction qui sont différentes des valeurs calculées à des niveaux de compatibilité antérieurs. Après la mise à niveau vers le niveau de compatibilité 110, vous pouvez être amené à reconstruire les index, les segments de mémoire ou les contraintes CHECK qui utilisent la fonction SOUNDEX. Pour plus d’informations, consultez [SOUNDEX &#40;Transact-SQL&#41;](/sql/t-sql/functions/soundex-transact-sql).
|Message de nombre de lignes pour les échecs d'instructions DML|Dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], le [!INCLUDE[ssDE](../includes/ssde-md.md)] envoie régulièrement le jeton TDS DONE avec RowCount: 0 aux clients lorsqu'une instruction DML échoue. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], la valeur incorrecte -1 est envoyée au client lorsque l'instruction DML qui échoue est contenue dans un bloc TRY-CATCH ou est automatiquement paramétrable par le [!INCLUDE[ssDE](../includes/ssde-md.md)] ou lorsque le bloc TRY-CATCH n'est pas au même niveau que l'instruction qui échoue. Par exemple, si un bloc TRY-CATCH appelle une procédure stockée et une instruction DML dans la procédure échoue, le client ne reçoit pas correctement la valeur -1.<br /><br /> Les applications qui reposent sur ce comportement incorrect échouent.|  
|SERVERPROPERTY ('édition')|Édition du produit installée de l'instance de [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]. Utilisez la valeur de cette propriété pour déterminer les fonctionnalités et les limites, par exemple le nombre maximal de processeurs qui sont pris en charge par le produit installé.<br /><br /> En fonction de l’édition Enterprise installée, elle peut retourner « Enterprise Edition » ou « Enterprise Edition : Core-based Licensing ». Les éditions Enterprise sont différenciées selon la capacité maximale de calcul par une seule instance de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d’informations sur les limites de capacité [!INCLUDE[ssSQL11](../includes/sssql11-md.md)]de calcul dans, consultez [Compute Capacity Limits by Edition of SQL Server](../sql-server/compute-capacity-limits-by-edition-of-sql-server.md).|  
|CREATE LOGIN|L' `CREATE LOGIN WITH PASSWORD = '`option *Password* `' HASHED` ne peut pas être utilisée avec les hachages créés par [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] 7 ou une version antérieure.|  
|Opérations CAST et CONVERT pour `datetimeoffset`|Les seuls styles pris en charge lors de la conversion des types de date et d'heure en `datetimeoffset` sont 0 ou 1. Tous les autres styles de conversion retournent l'erreur 9809. Par exemple, le code suivant retourne une erreur 9809.<br /><br /> `SELECT CONVERT(date, CAST('7070-11-25 16:25:01.00986 -02:07' as datetimeoffset(5)), 107);`|  
  
### <a name="dynamic-management-views"></a>Vues de gestion dynamique  
  
|Affichage|Description|  
|----------|-----------------|  
|sys.dm_exec_requests|La colonne de commande passe de `nvarchar(16)` à `nvarchar(32)`.|  
|sys.dm_os_memory_cache_counters|Les colonnes suivantes ont été renommées :<br /><br /> single_pages_kb est désormais : <br />                          pages_kb<br /><br /> multi_pages_kb<br />                           est maintenant : pages_in_use_kb|  
|sys.dm_os_memory_cache_entries|La colonne pages_allocated_count colonne a été renommée pages_kb.|  
|sys.dm_os_memory_clerks|La colonne multi_pages_kb a été supprimée.<br /><br /> La colonne single_pages_kb colonne a été renommée pages_kb.|  
|sys.dm_os_memory_nodes|Les colonnes suivantes ont été renommées :<br /><br /> single_pages_kb est désormais : <br />                            pages_kb<br /><br /> multi_pages_kb est désormais : <br />                            foreign_committed_kb|  
|sys.dm_os_memory_objects|Les colonnes suivantes ont été renommées.<br /><br /> pages_allocated_count est désormais :<br />                            pages_in_bytes<br /><br /> max_pages_allocated_count est maintenant : max_pages_in_bytes|  
|sys.dm_os_sys_info|Les colonnes suivantes ont été renommées :<br /><br /> physical_memory_in_bytes est désormais : <br />                            physical_memory_kb<br /><br /> bpool_commit_target est désormais : <br />                            committed_target_kb<br /><br /> bpool_visible est désormais : <br />                            visible_target_kb<br /><br /> virtual_memory_in_bytes est désormais : <br />                            virtual_memory_kb<br /><br /> bpool_commited est désormais :<br />                            committed_kb|  
|sys.dm_os_workers|La colonne de paramètres régionaux a été supprimée.|  
  
### <a name="catalog-views"></a>Affichages catalogue  
  
|Affichage|Description|  
|----------|-----------------|  
|sys.data_spaces<br /><br /> sys.partition_schemes<br /><br /> sys.filegroups<br /><br /> sys.partition_functions|Une nouvelle colonne, is_system, a été ajoutée à sys.data_spaces et sys.partition_functions. (sys.partition_schemes et sys.filegroups héritent des colonnes de sys.data_spaces.)<br /><br /> La valeur 1 dans cette colonne indique que l'objet est utilisé pour les fragments d'index de recherche en texte intégral.<br /><br /> Dans sys.partition_functions, sys.partition_schemes et sys.filegroups, la nouvelle colonne n'est pas la dernière colonne. Modifiez les requêtes existantes qui reposent sur l'ordre des colonnes retournées par ces affichages catalogue.|  
  
### <a name="sql-clr-data-types-geometry-geography-and-hierarchyid"></a>Types de données SQL CLR (geometry, geography et hierarchyid)  
 L’assembly **Microsoft. SqlServer. types. dll**, qui contient les types de données spatiales et le type hierarchyid, a été mis à niveau de la version 10,0 vers la version 11,0. Les applications personnalisées qui font référence à cet assembly peuvent échouer lorsque les conditions suivantes sont remplies.  
  
-   Lorsque vous déplacez une application personnalisée à partir d’un ordinateur [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)] sur lequel est installé sur un ordinateur sur [!INCLUDE[ssCurrent](../includes/sscurrent-md.md)] lequel seul est installé, l’application échoue, car la version référencée 10,0 de l’assembly **SqlTypes** n’est pas présente. Ce message d'erreur peut s'afficher : `"Could not load file or assembly 'Microsoft.SqlServer.Types, Version=10.0.0.0, Culture=neutral, PublicKeyToken=89845dcd8080cc91' or one of its dependencies. The system cannot find the file specified."`  
  
-   Lorsque vous référencez l’assembly **SqlTypes** version 11,0 et que la version 10,0 est également installée, le message d’erreur suivant peut s’afficher :`"System.InvalidCastException: Unable to cast object of type 'Microsoft.SqlServer.Types.SqlGeometry' to type 'Microsoft.SqlServer.Types.SqlGeometry'."`  
  
-   Quand vous référencez la version 11,0 de l’assembly **SqlTypes** à partir d’une application personnalisée qui cible .net 3,5, 4 ou 4,5, l’application échoue, car SqlClient par conception charge la version 10,0 de l’assembly. Cette erreur se produit lorsque l'application appelle l'une des méthodes suivantes :  
  
    -   méthode `GetValue` de la classe `SqlDataReader`  
  
    -   méthode `GetValues` de la classe `SqlDataReader`  
  
    -   opérateur d'index de crochets [] de la classe `SqlDataReader`  
  
    -   méthode `ExecuteScalar` de la classe `SqlCommand`  
  
 Vous pouvez contourner ce problème en utilisant l’une des méthodes suivantes :  
  
-   Vous pouvez contourner ce problème dans votre code en appelant la méthode `GetSqlBytes`, au lieu des méthodes Get répertoriées ci-dessus, pour extraire les types de systèmes CLR [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], comme le montre l'exemple suivant :  
  
    ```csharp  
    string query = "SELECT [SpatialColumn] FROM [SpatialTable]";  
          using (SqlConnection conn = new SqlConnection("..."))  
          {  
                SqlCommand cmd = new SqlCommand(query, conn);  
  
                conn.Open();  
                SqlDataReader reader = cmd.ExecuteReader();  
  
                while (reader.Read())  
                {  
                      // In version 11.0 only  
                      SqlGeometry g =   
    SqlGeometry.Deserialize(reader.GetSqlBytes(0));  
  
                      // In version 10.0 or 11.0  
                      SqlGeometry g2 = new SqlGeometry();  
                      g.Read(new BinaryReader(reader.GetSqlBytes(0).Stream));  
                }  
          }  
    ```  
  
-   Vous pouvez contourner ce problème en utilisant la redirection d'assembly dans le fichier de configuration de l'application, comme le montre l'exemple suivant :  
  
    ```xml  
    <runtime>  
    <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">  
        ...  
        <dependentAssembly>  
            <assemblyIdentity name="Microsoft.SqlServer.Types" publicKeyToken="89845dcd8080cc91" culture="neutral" />  
            <bindingRedirect oldVersion="10.0.0.0" newVersion="11.0.0.0" />  
        </dependentAssembly>  
        ...  
    </assemblyBinding>  
    <runtime>  
    ```  
  
-   Vous pouvez contourner ce problème dans votre chaîne de connexion en spécifiant la valeur « SQL Server 2012 » pour que de l'attribut « Type System Version » force SqlClient à charger la version 11.0 de l'assembly. Cet attribut de chaîne de connexion est uniquement disponible dans le .NET 4.5 et versions ultérieures.  
  
-   La balise `assemblyBinding` doit être encapsulée sous la balise `runtime`.  
  
### <a name="support-for-awe"></a>Prise en charge d'AWE  
 La prise en charge d'AWE (Address Windowing Extensions) 32 bits a été arrêtée. Cela peut entraîner une baisse des performances sur les systèmes d'exploitation 32 bits. Pour les installations utilisant de grandes quantités de mémoire, migrez vers un système d'exploitation 64 bits.  
  
### <a name="xquery-functions-are-surrogate-aware"></a>Les fonctions XQuery prennent en charge la substitution  
 La recommandation du W3C pour les fonctions et les opérateurs XQuery exigent qu'ils prennent en charge une paire de substitution qui représente un caractère Unicode à plage élevée en tant que glyphe unique dans l'encodage UTF-16. Toutefois, dans les versions de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] antérieures à [!INCLUDE[ssSQL11](../includes/sssql11-md.md)], les fonctions de chaîne ne reconnaissaient pas les paires de substitution comme caractère unique. Certaines opérations de chaîne, telles que les calculs de longueur de chaîne et les extractions de sous-chaînes, ont retourné des résultats incorrects. [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] prend désormais entièrement en charge UTF-16 et la gestion correcte des paires de substitution.  
  
 Le type de données XML dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] autorise uniquement les paires de substitution bien formées. Toutefois, certaines fonctions peuvent toujours retourner des résultats indéfinis ou inattendus dans certaines circonstances, étant donné qu'il est possible de passer des paires de substitution non valides ou partielles aux fonctions XQuery comme valeurs de chaîne. Tenez compte des méthodes suivantes pour générer des valeurs de chaîne en utilisant XQuery dans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] :  
  
-   Fournissez une valeur de chaîne constante comme valeur binaire. Lorsque vous utilisez cette méthode, il est possible de passer des paires de substitution non valides ou partielles.  
  
-   Fournissez une valeur de chaîne constante en fournissant des entités de caractère. Lorsque vous utilisez cette méthode, il est impossible de passer des paires de substitution non valides. Les fonctions XQuery requièrent une entité de caractère unique pour le caractère de niveau supérieur. Ces fonctions génèrent une erreur si les entités de caractère pour les caractères de paire de substitution sont fournies.  
  
-   Importez des valeurs externes à l’aide de **SQL : column** ou **SQL : variable**. En utilisant ces méthodes, il est possible d'introduire des paires de substitution non valides ou partielles.  
  
#### <a name="affected-xquery-functions-and-operators"></a>Fonctions et opérateurs XQuery affectés  
 Les fonctions et opérateurs XQuery suivants gèrent maintenant les paires de substitution UTF-16 correctement dans [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] :  
  
-   **FN : String-length**. Toutefois, si une paire de substitution non valide ou partielle est passée comme argument, le comportement de **String-length** n’est pas défini.  
  
-   **FN : sous-chaîne**.  
  
-   **FN : contient**. Toutefois, si une paire de substitution partielle est passée comme valeur, **Contains** peut retourner des résultats inattendus, car elle peut trouver la paire de substitution partielle contenue dans une paire de substitution correcte.  
  
-   **FN : Concat**. Toutefois, si une paire de substitution partielle est passée comme valeur, **concat** peut produire des paires de substitution incorrectes ou des paires de substitution partielles.  
  
-   Opérateurs de comparaison et clause **order by** . Les opérateurs de comparaison incluent \<+,, \<>, =, >`eq`= `lt`, `gt`, `le`,, `ge`et.  
  
#### <a name="distributed-query-calls-to-a-system-procedure"></a>Appels de requête distribuée à une procédure système  
 Les appels de requête distribuée via `OPENQUERY` à certaines procédures système échouent lorsque l'appel est effectué d'un serveur [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] à un autre. Ceci se produit lorsque le [!INCLUDE[ssDE](../includes/ssde-md.md)] ne peut pas découvrir les métadonnées pour une procédure. Par exemple, `SELECT * FROM OPENQUERY(..., 'EXEC xp_loginfo')`.  
  
#### <a name="isolation-level-and-sp_reset_connection"></a>Niveau d'isolement et sp_reset_connection  
 Le niveau d'isolement pour les connexions est géré par les pilotes clients de la manière suivante :  
  
-   Tous les pilotes natifs (SNAC, MDAC, ODBC) définissent le niveau d'isolement (selon les paramètres de l'application) lors de l'exécution de sp_reset_connection.  
  
-   Pour ADO.NET, vous obtiendrez essentiellement un niveau d'isolement aléatoire en fonction de la connexion obtenue à partir du pool (si l'application utilise un niveau d'isolement différent). Étant donné que le pool ADO.NET peut recycler les connexions en interne de façon transparente, vous ne pouvez pas prédire quelle connexion vous obtiendrez du pool.  
  
-   Avec le pilote JDBC, le comportement est le même que pour ADO.NET  
  
     L'application doit toujours définir explicitement le niveau d'isolement après l'ouverture de la connexion pour obtenir ce qu'elle veut.  
  
     Comme la connexion JDBC peut être regroupée dans un pool, il est possible que l'application obtienne un niveau d'isolement aléatoire sans le savoir.  
  
 Pour maintenir la compatibilité descendante, ce nouveau comportement concerne uniquement les clients récents (à partir de TDS 7.4).  
  
#### <a name="backward-compatibility"></a>Backward Compatibility  
 **Le nouveau comportement dépend du niveau de compatibilité**  
  
 Les fonctions et opérateurs suivants illustrent le nouveau comportement décrit ci-dessus uniquement lorsque le niveau de compatibilité est supérieur ou égal à 110 :  
  
-   **FN : contient**.  
  
-   **FN : Concat**.  
  
-   opérateurs de comparaison et clause **order by**  
  
 **Le nouveau comportement dépend de l'URI d'espace de noms par défaut des fonctions**  
  
 Les fonctions suivantes illustrent le nouveau comportement décrit ci-dessus uniquement lorsque l’URI d’espace de noms par défaut correspond à l’espace de [http://www.w3.org/2005/xpath-functions](http://www.w3.org/2005/xpath-functions)noms dans la recommandation finale, autrement dit,. Lorsque le niveau de compatibilité est supérieur ou égal à 110, alors par défaut [!INCLUDE[ssSQL11](../includes/sssql11-md.md)] lie l'espace de noms de fonction par défaut à cet espace de noms. Toutefois ces fonctions illustrent le nouveau comportement lorsque cet espace de noms est utilisé quel que soit le niveau de compatibilité.  
  
-   **fn:string-length**  
  
-   **FN : SUBSTRING**  
  
##  <a name="breaking-changes-in-sql-server-2008sql-server-2008r2"></a><a name="KJKatmai"></a>Dernières modifications dans SQL Server 2008/SQL Server 2008R2  
 Cette section contient les modifications avec rupture introduites dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Aucune modification n'a été introduite dans [!INCLUDE[ssKilimanjaro](../includes/sskilimanjaro-md.md)].  
  
### <a name="collations"></a>Classements  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Nouveaux classements|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] introduit de nouveaux classements qui sont en alignement complet avec les classements fournis par Windows Server 2008. Ces 80 nouveaux classements présentent une précision linguistique améliorée et sont dénotés par des références de version *_100. Si vous choisissez un nouveau classement pour votre serveur ou base de données, gardez à l'esprit que le classement peut ne pas être reconnu par les clients équipés de pilotes clients plus anciens. En raison des classements non reconnus, l'application peut retourner des erreurs et échouer. Envisagez les solutions suivantes :<br /><br /> Mettez à niveau le système d'exploitation du client afin de mettre aussi à jour les classements du système sous-jacent.<br /><br /> Si le client est équipé du logiciel client de base de données, envisagez de lui appliquer une mise à jour du service.<br /><br /> Choisissez un classement existant qui établit un mappage à une page de codes du client.|  
  
### <a name="common-language-runtime-clr"></a>Common Language Runtime (CLR)  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Assemblys CLR|Lorsqu'une base de données est mise à niveau vers [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], l'assembly `Microsoft.SqlServer.Types` destiné à prendre en charge de nouveaux types de données est automatiquement installé. Les règles du Conseiller de mise à niveau détectent tout type d'utilisateur ou assembly avec des noms en conflit. Le Conseiller de mise à niveau recommandera de renommer tout assembly incompatible, et de renommer tout type en conflit ou d'utiliser des noms en deux parties dans le code pour faire référence à ce type d'utilisateur préexistant.<br /><br /> Si une mise à niveau de base de données détecte un assembly utilisateur avec un nom en conflit, elle renommera automatiquement cet assembly et placera la base de données en mode suspect.<br /><br /> Si un type d'utilisateur avec un nom en conflit existe pendant la mise à niveau, aucune étape spéciale n'est suivie. Après la mise à niveau, l'ancien type d'utilisateur et le nouveau type de système existeront tous deux. Le type d'utilisateur sera disponible uniquement en utilisant des noms en deux parties.|  
|Assemblys CLR|[!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] installe .NET Framework 3.5 SP1, qui met à jour les bibliothèques dans le GAC (Global Assembly Cache). Si des bibliothèques non prises en charge sont inscrites dans une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], votre application [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] peut cesser de fonctionner après la mise à niveau vers [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Cela est dû au fait que la maintenance ou la mise à niveau de bibliothèques dans le GAC ne met pas à jour les assemblys à l'intérieur de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. S'il existe un assembly dans une base de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] et dans le GAC, les deux copies de l'assembly doivent être exactement les mêmes. Si ce n'est pas le cas, une erreur se produit lorsque l'assembly est utilisé par l'intégration du CLR [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)]. Pour plus d’informations, consultez [.NET Framework les bibliothèques prises en charge](../relational-databases/clr-integration/database-objects/supported-net-framework-libraries.md).<br /><br /> Après la mise à niveau de votre base de données, effectuez la maintenance ou la mise à niveau de la copie de l'assembly à l'intérieur de vos bases de données [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] avec l'instruction ALTER ASSEMBLY. Pour plus d’informations, consultez [l’article 949080](https://go.microsoft.com/fwlink/?LinkId=154563)de la base de connaissances.<br /><br /> Exécutez la requête suivante dans votre base de données pour détecter si vous utilisez une bibliothèque .NET Framework non prise en charge dans votre application.<br /><br /> `SELECT name FROM sys.assemblies WHERE clr_name LIKE '%publickeytoken=b03f5f7f11d50a3a,%';`|  
|Routines CLR|Le recours à l'emprunt d'identité dans des fonctions CLR définies par l'utilisateur, des agrégats définis par l'utilisateur ou des types définis par l'utilisateur (UDT) peut entraîner une défaillance de votre application avec l'erreur 6522 suite à une mise à niveau vers [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Les scénarios suivants réussissent dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] mais échouent dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Des résolutions sont fournies pour chaque scénario.<br /><br /> Une fonction CLR définie par l’utilisateur, un agrégat défini par l’utilisateur ou une méthode UDT qui utilise l’emprunt d’identité a `nvarchar(max)`un `varchar(max)`paramètre `varbinary(max)`de `ntext`type `text`, `image`,,,, ou un UDT volumineux, et n’a pas l’attribut **DataAccessKind. Read** sur la méthode. Pour résoudre ce problème, ajoutez l’attribut **DataAccessKind. Read** sur la méthode, recompilez l’assembly et redéployez la routine et l’assembly.<br /><br /> Fonction table CLR qui a une méthode **init** qui effectue l’emprunt d’identité. Pour résoudre ce problème, ajoutez l’attribut **DataAccessKind. Read** sur la méthode, recompilez l’assembly et redéployez la routine et l’assembly.<br /><br /> Fonction table CLR qui a une méthode **FillRow** qui effectue l’emprunt d’identité. Pour résoudre ce problème, supprimez l’emprunt d’identité de la méthode **FillRow** . N’accédez pas aux ressources externes à l’aide de la méthode **FillRow** . Au lieu de cela, accédez à des ressources externes à partir de la méthode **init** .|  
  
### <a name="dynamic-management-views"></a>Vues de gestion dynamique  
  
|Affichage|Description|  
|----------|-----------------|  
|sys.dm_os_sys_info|Suppression des colonnes cpu_ticks_in_ms et sqlserver_start_time_cpu_ticks.|  
|sys. dm_exec_query_resource_semaphoressys. dm_exec_query_memory_grants|La colonne resource_semaphore_id n'est pas un ID unique dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Cette modification peut affecter l'exécution de la requête de résolution des problèmes. Pour plus d’informations, consultez [sys. dm_exec_query_resource_semaphores &#40;Transact-SQL&#41;](/sql/relational-databases/system-dynamic-management-views/sys-dm-exec-query-resource-semaphores-transact-sql).|  
  
### <a name="errors-and-events"></a>Erreurs et événements  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Erreurs de connexion|Dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], l'erreur 18452 est retournée lorsqu'une connexion SQL est utilisée pour la connexion à un serveur configuré pour utiliser uniquement l'authentification Windows. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], l'erreur 18456 est retournée à la place.|  
  
### <a name="showplan"></a>Showplan  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Schéma du plan d'exécution XML|Un nouvel élément **SeekPredicateNew** est ajouté au schéma Showplan XML, et la séquence XSD englobante (**SqlPredicatesType**) est convertie en élément ** \<>xsd : Choice** . Au lieu d’un ou plusieurs éléments **SeekPredicate** , un ou plusieurs éléments **SeekPredicateNew** peuvent désormais apparaître dans le Showplan XML. Les deux éléments s'excluent mutuellement. **SeekPredicate** est conservé dans le schéma Showplan XML à des fins de compatibilité descendante. Toutefois, les plans de requête [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] créés dans peuvent contenir l’élément **SeekPredicateNew** . Les applications qui s’attendent à récupérer uniquement l’enfant **SeekPredicate** à partir du nœud ShowplanXml/BatchSequence/batch/States/StmtSimple/QueryPlan/RelOp/IndexScan/SeekPredicates peuvent échouer si l’élément **SeekPredicate** n’existe pas. Réécrivez l’application pour qu’elle attende l’élément **SeekPredicate** ou **SeekPredicateNew** dans ce nœud. Pour plus d'informations, consultez .|  
|Schéma du plan d'exécution XML|Un nouvel attribut **IndexKind** est ajouté au type complexe **ObjectType** dans le schéma Showplan XML. Les applications qui valident de façon stricte les plans [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] sur le schéma [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)] échouent.|  
  
### <a name="transact-sql"></a>Transact-SQL  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Événement DDL ALTER_AUTHORIZATION_DATABASE|Dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], lorsque l’événement DDL ALTER_AUTHORIZATION_DATABASE se déclenche, la valeur « Object » est retournée dans l’élément **OBJECTTYPE** du XML EventData pour cet événement lorsque le type d’entité de l’élément sécurisable dans l’opération DDL (Data Definition Language) est un objet. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], le type réel (par exemple, « table » ou « function ») est retourné.|  
|CONVERT|Si un style non valide est passé à la fonction CONVERT, une erreur est retournée lorsque la conversion est de type binaire à caractère ou caractère à binaire. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], le style non valide est défini sur le style par défaut pour les conversions binaire à caractère et caractère à binaire.|  
|GRANT/DENY/REVOKE EXECUTE sur les assemblys|L'autorisation EXECUTE ne peut pas être accordée, révoquée ou refusée sur les assemblys. Cette autorisation n'a aucun effet et provoque à présent une erreur. Accordez, refusez ou révoquez une autorisation EXECUTE sur les procédures stockées ou fonctions qui font plutôt référence à la méthode d'assembly.|  
|Autorisations GRANT/DENY/REVOKE sur les types de systèmes|Les autorisations ne peuvent pas être accordées, révoquées ou refusées sur les types de systèmes. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], ces instructions sont correctement exécutées, mais n'ont aucun effet. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], une erreur est retournée.|  
|GROUP BY|La clause GROUP BY ne peut pas contenir de sous-requête dans une expression utilisée pour la liste GROUP BY. Dans les versions antérieures de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)], cela était autorisé. Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], l'erreur 144 est retournée.<br /><br /> Par exemple, le code suivant réussit dans SQL Server 2005 et échoue dans SQL Server 2008.<br /><br /> `DECLARE @Test TABLE(a int NOT NULL);` <br /> `INSERT INTO @Test SELECT 1 union ALL SELECT 2;` <br /> `SELECT COUNT(*)` <br /> `FROM @Test` <br /> `GROUP BY CASE WHEN a IN (SELECT t.a FROM @Test AS t)` <br /> `THEN 1 ELSE 0` <br /> `END;`|  
|Clause OUTPUT|Pour empêcher tout comportement non déterministe, la clause OUTPUT ne peut pas référencer une colonne d'une vue ou fonction table lorsque cette colonne est définie par l'une des méthodes suivantes :<br /><br /> Une sous-requête.<br /><br /> Une fonction définie par l'utilisateur qui offre un accès à des données utilisateur ou système, ou qui est supposée permettre d'y accéder.<br /><br /> Une colonne calculée qui contient une fonction définie par l'utilisateur qui offre un accès aux données utilisateur ou système dans sa définition.<br /><br /> <br /><br /> Quand [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] détecte une telle colonne dans la clause OUTPUT, l’erreur 4186 est générée. Pour plus d’informations, consultez [MSSQLSERVER_4186](../relational-databases/errors-events/mssqlserver-4186-database-engine-error.md).|  
|Clause OUTPUT INTO|La table cible de la clause OUTPUT INTO ne peut pas comporter de déclencheurs activés.|  
|Option de niveau serveur precompute rank|Cette option n'est pas prise en charge dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)]. Modifiez dès que possible les applications qui utilisent actuellement cette fonction.|  
|READPAST, indicateur de table|Vous ne pouvez pas spécifier l'indicateur READPAST sous l'isolement d'instantané.<br /><br /> L'indicateur READPAST est ignoré lorsque l'option de base de données READ_COMMITED_SNAPSHOT ou ALLOW_SNAPSHOT_ISOLATION est activée (ON). Toutefois, si vous combinez l'indicateur READPAST avec READCOMMITTEDLOCK, le comportement de READPAST correspond à l'indicateur de blocage READCOMMITTED.|  
|sp_helpuser|Les noms de colonnes suivants qui sont retournés dans le jeu de résultats de la procédure stockée sp_helpuser ont été modifiés :<br /><br /> GroupName est maintenant :<br />                            RoleName<br /><br /> Group_name est désormais :<br />                            Role_name<br /><br /> Group_id est désormais :<br />                            Role_id<br /><br /> Users_in_group est désormais :<br />                            Users_in_role|  
|chiffrement transparent des données|Le chiffrement transparent des données est effectué au niveau d'E/S : la structure de page est non chiffrée en mémoire et chiffrée uniquement lorsque la page est écrite sur disque. Les fichiers de bases de données et les fichiers journaux sont tous deux chiffrés. Les applications tierces qui ignorent le mécanisme [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] standard pour accéder aux pages (par exemple, en analysant directement les fichiers de données ou journaux) échouent lorsqu'une base de données utilise le chiffrement transparent des données, car les données sont chiffrées dans les fichiers. De telles applications peuvent exploiter l'API de chiffrement Windows pour développer une solution pour déchiffrer les données à l'extérieur de [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)].|  
  
### <a name="xquery"></a>XQuery  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Prise en charge de la date et de l'heure|Dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], les types `xs:time`de données `xs:date`, et `xs:dateTime` ne prennent pas en charge les fuseaux horaires. Les données de fuseau horaire sont mappées au fuseau horaire UTC. [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)] présente un comportement conforme standard qui a pour conséquence les modifications suivantes :<br /><br /> Les valeurs sans fuseau horaire sont validées.<br /><br /> Le fuseau horaire fourni ou l'absence de fuseau horaire est un paramètre conservé.<br /><br /> La représentation de stockage interne est modifiée.<br /><br /> La résolution des valeurs stockées est augmentée.<br /><br /> Les années négatives ne sont pas autorisées.<br /><br /> <br /><br /> Remarque : modifiez les applications et les expressions XQuery pour prendre en compte les nouvelles valeurs de type.|  
|Expressions XQuery et XPath|Dans [!INCLUDE[ssVersion2005](../includes/ssversion2005-md.md)], les étapes d’une expression XQuery ou XPath qui commencent par un signe deux-points («  : ») sont autorisées. Par exemple, l'instruction suivante contient un test de nom (`CTR02)` dans l'expression XPath qui commence par un signe deux-points.<br /><br /> `SELECT FileContext.query('for n$ in //CTR return <C>{data )(n$/:CTR02)} </C>) AS Files FROM dbo.MyTable;`<br /><br /> Dans [!INCLUDE[ssKatmai](../includes/sskatmai-md.md)], cette utilisation est rejetée, car elle n'est pas conforme aux normes XML. L'erreur 9341 est retournée. Supprimez le signe deux-points de début ou spécifiez un préfixe pour le test de nom, par exemple (n$/CTR02) ou (n$/p1:CTR02).|  
  
### <a name="connecting"></a>Connecting  
  
|Fonctionnalité|Description|  
|-------------|-----------------|  
|Connexion depuis [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client à l'aide de SSL|Lors de la connexion à [!INCLUDE[ssNoVersion](../includes/ssnoversion-md.md)] Native Client, les applications qui utilisent "SERVER=shortname; FORCE ENCRYPTION=true" avec un certificat dont les objets spécifient des noms de domaine complet (FQDN) se sont connectées par le passé en raison d'une validation souple. SQL Server 2008 R2 améliore la sécurité en mettant en vigueur des objets de nom de domaine complet pour les certificats. Les applications qui reposent sur une validation souple doivent entreprendre l'une des actions suivantes :<br /><br /> Utiliser le nom de domaine complet dans la chaîne de connexion.<br /><br /> -Cette option ne nécessite pas la recompilation de l’application si le mot clé SERVER de la chaîne de connexion est configuré à l’extérieur de l’application.<br /><br /> -Cette option ne fonctionne pas pour les applications dont les chaînes de connexion sont codées en dur.<br /><br /> -Cette option ne fonctionne pas pour les applications qui utilisent la mise en miroir de bases de données dans la mesure où le serveur mis en miroir répond avec un nom simple.|  
||Ajouter un alias pour le nom court à mapper sur le nom de domaine complet.<br /><br /> : Cette option fonctionne même pour les applications dont les chaînes de connexion sont codées en dur.<br /><br /> -Cette option ne fonctionne pas pour les applications qui utilisent la mise en miroir de bases de données, car les fournisseurs ne recherchent pas les alias pour les noms de partenaires de basculement reçus.|  
||Faire en sorte qu'un certificat soit émis pour le nom court.<br /><br /> : Cette option fonctionne pour toutes les applications.|  

## <a name="breaking-changes-in-sql-server-2005"></a><a name="Yukon"></a>Modifications avec rupture dans SQL Server 2005  

[!INCLUDE[Archived documentation for very old versions of SQL Server](../includes/paragraph-content/previous-versions-archive-documentation-sql-server.md)]

## <a name="see-also"></a>Voir aussi  
 [Fonctionnalités de Moteur de base de données dépréciées dans SQL Server 2014](deprecated-database-engine-features-in-sql-server-2016.md?view=sql-server-2014)   
 [Changements de comportement des fonctionnalités de Moteur de base de données dans SQL Server 2014](../../2014/database-engine/behavior-changes-to-database-engine-features-in-sql-server-2014.md?view=sql-server-2014)   
 [Fonctionnalités de Moteur de base de données abandonnées dans SQL Server 2014](discontinued-database-engine-functionality-in-sql-server-2016.md?view=sql-server-2014)   
 [Compatibilité descendante du moteur de base de données SQL Server](sql-server-database-engine-backward-compatibility.md)   
 [Niveau de compatibilité ALTER DATABASE &#40;Transact-SQL&#41;](/sql/t-sql/statements/alter-database-transact-sql-compatibility-level)  
 [Dernières modifications apportées aux fonctionnalités des outils d'administration dans SQL Server 2014](breaking-changes-to-management-tools-features-in-sql-server-2014.md?view=sql-server-2014)  
  
